---
platform: android
title: Files Written to External Storage
type: [dynamic]
---

## Overview

The goal of this test is to retrieve the files written to the external storage and inspect them regardless of the APIs used to write them. It uses a simple approach based on [file retrieval from the device storage](/MASTG/techniques/android/MASTG-TECH-0002) before and after the app is exercised to identify the files created during the app's execution and to check if they contain sensitive data.

## Steps

1. Make sure you have [adb](/MASTG/tools/android/MASTG-TOOL-0004) installed.
2. [Install the app](/MASTG/techniques/android/MASTG-TECH-0005).
3. Before running the app, [get the current list of files](/MASTG/techniques/android/MASTG-TECH-0002) in the external storage.
4. Exercise the app.
5. After running the app, retrieve the list of files in the external storage again.
6. Calculate the difference between the two lists.

## Observation

The output should contain a list of files that were created on the external storage during the app's execution.

## Evaluation

The test case fails if the files found above are not encrypted and leak sensitive data.

To confirm this, you can [reverse engineer the app](/MASTG/techniques/android/MASTG-TECH-0017) and [inspect the code](/MASTG/techniques/android/MASTG-TECH-0023).
