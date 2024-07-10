# utmsnap

`utmsnap` is a Bash script for managing snapshots of UTM virtual machines. It allows you to create, revert, list, prune, and delete snapshots.

## Usage

```bash
./utmsnap {create|revert|ls|prune|delete} [arguments]
```

### Commands

#### create

Create a snapshot of the specified VM.

```bash
./utmsnap create <VM_NAME>
```

- `<VM_NAME>`: Name of the virtual machine.

#### revert

Revert a VM to a specified snapshot.

```bash
./utmsnap revert <VM_NAME> <SNAPSHOT_FILE>
```

- `<VM_NAME>`: Name of the virtual machine.
- `<SNAPSHOT_FILE>`: Snapshot file to revert to.

#### ls

List snapshots. Optionally, filter by VM name.

```bash
./utmsnap ls [VM_NAME]
```

- `[VM_NAME]`: (Optional) Name of the virtual machine.

#### prune

Prune snapshots, keeping only the specified number of recent snapshots for the VM.

```bash
./utmsnap prune <VM_NAME> <RETENTION>
```

- `<VM_NAME>`: Name of the virtual machine.
- `<RETENTION>`: Number of recent snapshots to retain.

#### delete

Delete a specified snapshot file.

```bash
./utmsnap delete <SNAPSHOT_FILE>
```

- `<SNAPSHOT_FILE>`: Snapshot file to delete.

### Example Usage

- Create a snapshot for `myvm`:

  ```bash
  ./utmsnap create myvm
  ```

- Revert `myvm` to snapshot `myvm_2024-07-10-12-30-00.tar.gz`:

  ```bash
  ./utmsnap revert myvm myvm_2024-07-10-12-30-00.tar.gz
  ```

- List all snapshots:

  ```bash
  ./utmsnap ls
  ```

- List snapshots for `myvm`:

  ```bash
  ./utmsnap ls myvm
  ```

- Prune snapshots for `myvm`, keeping only the latest 3:

  ```bash
  ./utmsnap prune myvm 3
  ```

- Delete snapshot `myvm_2024-07-10-12-30-00.tar.gz`:

  ```bash
  ./utmsnap delete myvm_2024-07-10-12-30-00.tar.gz
  ```

### Directory Structure

- Snapshots are stored in `~/Library/Containers/com.utmapp.UTM/Data/Documents/Snapshots`.

### Notes

- Ensure the `utmsnap` script has execute permissions:

  ```bash
  chmod +x ./utmsnap
  ```

- The script assumes the UTM VM directories are located under `~/Library/Containers/com.utmapp.UTM/Data/Documents`.

