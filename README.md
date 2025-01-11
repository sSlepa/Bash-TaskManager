# Task Manager in Bash

This project is a **Bash-based Task Manager**, designed for monitoring and managing system processes and configurations on UNIX/Linux systems. It provides an interactive command-line interface with various functionalities for system administration.

## Features

### 1. Help (`show_help`)

Displays a help message that explains how to use the script and the available options.

### 2. Resource Monitoring (`monitor_resources`)

Monitors system resources at a specified interval.

- Supports time units: seconds (`s`), minutes (`m`), and hours (`h`).
- Displays:
  - **RAM usage**
  - **Disk usage**
  - **CPU usage**
  - **Network traffic intensity**

Example usage:

```bash
./task_manager.sh -m 10s
```

### 3. Process Operations (`process_operations`)

Allows performing various operations on processes:

- **Start** new processes.
- **Suspend** a process by PID.
- **Wait** for current processes to finish.
- **Move** processes between background and foreground.

### 4. Configuration Changes (`change_config`)

Allows modifying system configurations using `sed` and `sysctl`:

- Change the **swappiness** parameter (0-100).
- Modify other `sysctl` parameters by editing `/etc/sysctl.conf`.

Example usage:

```bash
./task_manager.sh -c
```

### 5. Top Processes (`top_processes`)

Displays the top `N` processes by memory usage.

Example usage:

```bash
./task_manager.sh -t 5
```

### 6. Terminate Processes (`terminate_processes`)

Allows terminating processes using:

- **Soft kill**: Graceful termination.
- **Hard kill**: Force termination using `kill -9`.

Example usage:

```bash
./task_manager.sh -k soft
```

### 7. Restart Process (`restart_process`)

Restarts a specific process by its PID.

- Extracts the original command of the process using `ps`.
- Stops the process using `kill -9`.
- Restarts the process by running the extracted command.

Example usage:

```bash
./task_manager.sh -r <PID>
```

### 8. Show Logs (`show_logs`)

Displays system logs in real time using `tail -f /var/log/syslog`. The user can stop the log display by pressing `Ctrl+C`.

Example usage:

```bash
./task_manager.sh -l
```

### 9. Show Disk Usage (`show_disk_usage`)

Displays disk usage for top-level directories, sorted by size.

Example usage:

```bash
./task_manager.sh -u
```

## Command-Line Options

The script supports the following options:

| Option          | Description                                   |
| --------------- | --------------------------------------------- |
| `-m, --monitor` | Monitor resources at a specified interval.    |
| `-p, --process` | Perform various operations on processes.      |
| `-c, --config`  | Change system configurations.                 |
| `-t, --top`     | Show top `N` processes by memory usage.       |
| `-k, --kill`    | Terminate processes (soft or hard).           |
| `-r, --restart` | Restart a specific process by its PID.        |
| `-l, --log`     | Show system logs in real time.                |
| `-u, --usage`   | Display disk usage for top-level directories. |
| `-h, --help`    | Show the help message.                        |

## How to Run

1. Clone the repository.
2. Give execute permission to the script:
   ```bash
   chmod +x task_manager.sh
   ```
3. Run the script with the desired options:
   ```bash
   ./task_manager.sh [options]
   ```

## Example Usages

- Monitor system resources every 5 seconds:
  ```bash
  ./task_manager.sh -m 5s
  ```
- Display the top 3 processes by memory usage:
  ```bash
  ./task_manager.sh -t 3
  ```
- Terminate a process softly by PID:
  ```bash
  ./task_manager.sh -k soft
  ```
- Restart a process by PID:
  ```bash
  ./task_manager.sh -r 1234
  ```

## Requirements

- A UNIX/Linux system.
- `bash` shell.
- Root privileges for certain options (e.g., changing configurations, viewing logs).

## License

This project is licensed under the MIT License.

