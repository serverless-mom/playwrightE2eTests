# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Playwright end-to-end testing project configured for cross-browser testing on Chromium, Firefox, and WebKit. The project uses TypeScript and includes example tests for the Playwright website.

## Commands

### Running Tests
- `npx playwright test` - Run all tests
- `npx playwright test --headed` - Run tests in headed mode
- `npx playwright test --ui` - Run tests in UI mode
- `npx playwright test tests/example.spec.ts` - Run a specific test file
- `npx playwright test --grep "test name"` - Run tests matching a pattern

### Test Development
- `npx playwright codegen [url]` - Generate test code by recording interactions
- `npx playwright show-trace [trace-file]` - View test traces for debugging

### Browser Management
- `npx playwright install` - Install required browsers
- `npx playwright install-deps` - Install system dependencies for browsers

### Reporting
- `npx playwright show-report` - View HTML test report

## Architecture

The project follows Playwright's standard structure:

- `tests/` - Contains all test files (*.spec.ts)
- `playwright.config.ts` - Main configuration file
- Test files use the pattern `*.spec.ts` and import from `@playwright/test`

### Configuration Details
- Tests run in parallel by default (`fullyParallel: true`)
- Configured for three browser projects: Chromium, Firefox, WebKit
- HTML reporter generates reports in `playwright-report/`
- Traces are collected on first retry for failed tests
- CI environment runs with retries and single worker for stability

### Test Structure
Tests use Playwright's test runner with `test()` and `expect()` functions. Page objects and browser contexts are provided automatically through fixtures.