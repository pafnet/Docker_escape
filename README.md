# Docker Escape and Kubernetes Misconfiguration

This repository contains reports and findings related to Docker escape and Kubernetes misconfiguration vulnerabilities discovered during the security assessments. The reports are organized by tasks.

## Task 1: Docker Escape

**Flag:** `{5ec3f0fc9319702242d03f1e1684c113}`

**Report:**
1. **Initial Setup:** Launched the environment.
2. **File Exploration:** Used the `ls` command to check the available files in the container and found the `docker-escape` directory.
3. **Directory Inspection:** Inspected the `docker-escape` directory but found nothing significant.
4. **Hidden Files Check:** Used the `ll` command to view hidden files but found no sensitive information.
5. **Docker Socket Access:** Checked access to the `/var/run/docker.sock` file, which is used to communicate with the Docker daemon and can send commands to the Docker API.
6. **Privileged Container Creation:** Created a privileged container with access to the host filesystem using `docker.sock`.
7. **Flag Search:** Used the `find / -name "*flag*" 2>/dev/null` command to search for files and directories containing the word "flag" across the entire filesystem.
8. **Precise Search:** Narrowed down the search with `find /host -name "flag.txt"`.
9. **Flag Capture:** Found the `flag.txt` file and used the `cat` command to read and display the flag.

## Task 2: Kubernetes Misconfiguration

**Flag:** `{ ec67a837737d9aeb87c4751a27a047ad}`

**Report:**
1. **Initial Setup:** Launched the environment.
2. **Command History Check:** Started the investigation with the `history` command, as there were some commands in the history from the first task.
3. **ConfigMap Inspection:** Checked the last command `sudo kubectl get configmap myapp -o yaml` since ConfigMap can contain important configuration data for applications deployed in the cluster. Immediately found the flag.

---

This repository serves as a comprehensive guide to understanding and exploiting Docker escape and Kubernetes misconfiguration vulnerabilities. Each task is documented with detailed steps and findings.