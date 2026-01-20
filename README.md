# 📦 Package Management SOP (APT)

| Author        | Created On | Version   | Last Updated By | Internal Reviewer | Reviewer L0 | Reviewer L1 | Reviewer L2 |
|---------------|------------|-----------|-----------------|-------------------|-------------|-------------|-------------|
| Shobhit Goyal | 15-01-2026 | Version 1 | Shobhit Goyal   | 24-08-23          | —           | —           | —           |

---

## 📌 Introduction

**APT (Advanced Package Tool)** is a widely used package manager for **Debian-based Linux distributions** such as Ubuntu.  
This SOP provides a **standardized procedure** for installing, updating, upgrading, and removing software packages in a **consistent, secure, and reliable** manner.

---

## 📑 Table of Contents

- [📌 Introduction](#-introduction)  
- [🎯 Purpose](#-purpose)  
- [⭐ Key Features](#-key-features)  
- [✅ Pre-requisites](#-pre-requisites)  
- [📘 Software Overview](#-software-overview)  
- [💻 System Requirements](#-system-requirements)  
- [🌐 Important Ports](#-important-ports)  
- [🔗 Dependencies](#-dependencies)  
- [⚙️ Setup / Installation](#️-setup--installation)  
- [🔄 Updating Software](#-updating-software)  
- [🗑️ Removing Software](#️-removing-software)  
- [🚩 Common APT Flags](#-common-apt-flags)  
- [🛠️ Configuration](#️-configuration)  
- [🧹 Maintenance](#-maintenance)  
- [📊 Monitoring](#-monitoring)  
- [🛡️ Disaster Recovery](#️-disaster-recovery)  
- [⚡ High Availability](#-high-availability)  
- [🐞 Troubleshooting](#-troubleshooting)  
- [❓ FAQs](#-faqs)  
- [📞 Contact](#-contact)  
- [📚 References](#-references)  

---

## 🎯 Purpose

The purpose of this SOP is to define standardized steps for:

- Installing software packages  
- Updating package repositories  
- Upgrading installed software  
- Removing and cleaning unused packages  

This ensures **system stability, security, and ease of maintenance**.

---

## ⭐ Key Features

- Simple and efficient software installation  
- Automatic dependency management  
- Secure package verification  
- Centralized repository usage  
- Easy upgrade and rollback support  

---

## ✅ Pre-requisites

| Requirement     | Description                     |
|-----------------|---------------------------------|
| Operating System| Debian / Ubuntu-based Linux     |
| User Access     | Root or sudo privileges         |
| Network         | Internet access required        |

---

## 📘 Software Overview

| Software | Version              |
|----------|----------------------|
| APT      | Default system version |

---

## 💻 System Requirements

| Requirement | Minimum Recommendation |
|-------------|-------------------------|
| Processor   | Dual-Core               |
| RAM         | 2 GB or Higher          |
| Disk Space  | 5 GB or Higher          |
| OS Required | Ubuntu / Debian Linux   |

---

## 🌐 Important Ports

| Port | Description                                      |
|------|--------------------------------------------------|
| 22   | SSH access for remote package management         |
| 80/443 | Required for downloading packages from repos   |

---

## 🔗 Dependencies

### Run-time Dependencies

| Dependency | Version | Description                  |
|------------|---------|------------------------------|
| dpkg       | Default | Low-level package manager    |
| sudo       | Latest  | Privileged command execution |

### Other Dependencies

| Dependency          | Version | Description                  |
|---------------------|---------|------------------------------|
| ca-certificates     | Latest  | Secure package downloads     |
| apt-transport-https | Latest  | HTTPS repository support     |

---

## ⚙️ Setup / Installation

**Step-by-step Installation Instructions:**

- Update package repository
  
  ```bash
  sudo apt update
  ```
- Install a package

  ```bash
  sudo apt install <package-name>
  ```
- Install package without confirmation
   ```bash
   sudo apt install -y <package-name>
   ```
- Install specific version

  ```bash
  sudo apt install <package-name>=<version>
  ```

- Updating Software 
  
  | Command               | Description                         |
  |-----------------------|-------------------------------------|
  | sudo apt update       | Refresh package list                |
  | sudo apt upgrade      | Upgrade installed packages          |
  | sudo apt full-upgrade | Upgrade with dependency changes     |

- Removing Software
  
  | Command                          | Description                     |
  |----------------------------------|---------------------------------|
  | sudo apt remove <package-name>   | Remove package only              |
  | sudo apt purge <package-name>    | Remove package and config        |
  | sudo apt autoremove              | Remove unused dependencies       |
  | sudo apt clean                   | Clear downloaded cache           |

- Flag	Description

  | Flag        | Description                     |
  |-------------|---------------------------------|
  | -y          | Automatic yes to prompts         |
  | --dry-run   | Simulate without changes        |
  | -f          | Fix broken dependencies         |
  | --reinstall | Reinstall package               |

## APT configuration files are located under:

```bash
/etc/apt/
```
## Common files:

```bash
/etc/apt/sources.list
```
```bash
/etc/apt/sources.list.d/
```
## Always run:

```bash
sudo apt update
```
after modifying repository files.

## Maintenance
Task	Command
Update repository	sudo apt update
Upgrade system	sudo apt upgrade
Fix dependencies	sudo apt --fix-broken install
Clean cache	sudo apt clean

## Monitoring

- Verify package installation:

```bash 
dpkg -l | grep <package-name>
```
- Check logs:

```bash
/var/log/apt/history.log
/var/log/dpkg.log
```

## Disaster Recovery


Maintain regular system backups

Use --dry-run before major upgrades

Keep repository sources verified

Document package versions before upgrades

High Availability

Use automation tools (Ansible, scripts)

Maintain package version consistency across nodes

Use local mirrors for faster recovery

Perform rolling updates to avoid downtime

Troubleshooting
Issue	Cause	Solution
Package not found	Repository not updated	Run apt update
Broken dependencies	Interrupted install	Run apt -f install
Locked dpkg	Another process running	Remove lock & retry
FAQs

Is APT free to use?
Yes, it is open-source.

Can APT be used on all Linux distributions?
No, it is specific to Debian-based systems.

Does APT handle dependencies automatically?
Yes, dependencies are resolved automatically.

Contact Information
Name	Email Address
ABC	abc@mygurukulam.co
References
Links	Description
https://manpages.ubuntu.com/manpages/jammy/man8/apt.8.html
	Official APT documentation
https://wiki.debian.org/Apt
	Debian APT Guide
https://ubuntu.com/server/docs/package-management
	Ubuntu package management
