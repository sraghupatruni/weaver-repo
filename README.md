**Commands to Reproduce the Bug**

-----

### **Reproduction for Weaver Issue \#920: No Output Generated Despite Successful Execution**

This repository demonstrates a bug where the `weaver` tool executes successfully but fails to produce any output files.

### **Steps to Reproduce**

From the root of the repository, run the following commands.

1.  **Run the `generate` command:**
    Use the following command to generate the artifacts. (Absolute paths are used here to make it clear.)

    ```bash
    /weaver/target/release/weaver registry generate --registry /Users/dummy/telemetry --templates /Users/dummy/telemetry/templates markdown /Users/dummy/telemetry/docs
    ```

    **Expected Output:** The `docs` directory should be created with markdown files inside.

    **Actual Output:** The command runs and displays a success message, but no `docs` directory or files are created.

    ```text
    ✖ Debug is set to 0
    Generating artifacts for the registry `/Users/dummy/telemetry`
    ℹ Found registry manifest: /Users/dummy/telemetry/registry_manifest.yaml
    ✔ `telemetry` semconv registry `/Users/dummy/telemetry` loaded (2 files)
    ✔ No `before_resolution` policy violation
    ✔ `telemetry` semconv registry resolved
    ✔ No `after_resolution` policy violation
    ✔ Artifacts generated successfully
    ```

    I have also manually created the `docs` directory and set full permissions, but the command still did not produce the `.md` files as expected.

-----

2.  **Run the `update-markdown` command:**
    This is another attempt using the `update-markdown` command, which also fails to produce output.

    ```bash
    RUST_BACKTRACE=1 ~/weaver/target/release/weaver registry update-markdown --target markdown --registry ~/telemetry/ ~/telemetry/docs
    ```

    **Expected Output:** The `docs` directory should be created/updated with markdown files.

    **Actual Output:** The command shows a successful resolution but still produces no output files.

    ```text
    ✖ Debug is set to 0
    ℹ Found registry manifest: ~/telemetry/registry_manifest.yaml
    ✔ Registry resolved successfully
    Total execution time: 0.024928334s
    ```
