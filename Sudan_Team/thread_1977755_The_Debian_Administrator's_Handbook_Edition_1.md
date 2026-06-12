---
title: "The Debian Administrator's Handbook Edition 1"
date: 2012-05-10
forum: Sudan Team
---

### Post by suspect x on 2012-05-10
A reference book presenting the Debian distribution, from initial installation to configuration of services.

[COLOR="DarkOrange"]Book size:[/COLOR]
26MB
[COLOR="DarkOrange"]Book Download:[/COLOR]
[COLOR="Blue"][debian-handbook.pdf]("http://static.debian-handbook.info/download/stable/debian-handbook.pdf")
[/COLOR]
[COLOR="DarkOrange"]Book Contents:[/COLOR]
1. The Debian Project
1.1. What Is Debian?
1.1.1. A Multi-Platform Operating System
1.1.2. The Quality of Free Software
1.1.3. The Legal Framework: A Non-Profit Organization
1.2. The Foundation Documents
1.2.1. The Commitment towards Users
1.2.2. The Debian Free Software Guidelines
1.3. The Inner Workings of the Debian Project
1.3.1. The Debian Developers
1.3.2. The Active Role of Users
1.3.3. Teams and Sub-Projects
1.4. The Role of Distributions
1.4.1. The Installer: debian-installer
1.4.2. The Software Library
1.5. Lifecycle of a Release
1.5.1. The Experimental Status
1.5.2. The Unstable Status
1.5.3. Migration to Testing
1.5.4. The Promotion from Testing to Stable
2. Presenting the Case Study
2.1. Fast Growing IT Needs
2.2. Master Plan
2.3. Why a GNU/Linux Distribution?
2.4. Why the Debian Distribution?
2.4.1. Commercial and Community Driven Distributions
2.5. Why Debian Squeeze?
3. Analyzing the Existing Setup and Migrating
3.1. Coexistence in Heterogeneous Environments
3.1.1. Integration with Windows Machines
3.1.2. Integration with Mac OS machines
3.1.3. Integration with Other Linux/Unix Machines
3.2. How To Migrate
3.2.1. Survey and Identify Services
3.2.2. Backing up the Configuration
3.2.3. Taking Over an Existing Debian Server
3.2.4. Installing Debian
3.2.5. Installing and Configuring the Selected Services
4. Installation
4.1. Installation Methods
4.1.1. Installing from a CD-ROM/DVD-ROM
4.1.2. Booting from a USB Key
4.1.3. Installing through Network Booting
4.1.4. Other Installation Methods
4.2. Installing, Step by Step
4.2.1. Booting and Starting the Installer
4.2.2. Selecting the language
4.2.3. Selecting the country
4.2.4. Selecting the keyboard layout
4.2.5. Detecting Hardware
4.2.6. Loading Components
4.2.7. Detecting Network Hardware
4.2.8. Configuring the Network
4.2.9. Configuring the Clock
4.2.10. Administrator Password
4.2.11. Creating the First User
4.2.12. Detecting Disks and Other Devices
4.2.13. Starting the Partitioning Tool
4.2.14. Installing the Base System
4.2.15. Configuring the Package Manager (apt)
4.2.16. Debian Package Popularity Contest
4.2.17. Selecting Packages for Installation
4.2.18. Installing the GRUB Bootloader
4.2.19. Finishing the Installation and Rebooting
4.3. After the First Boot
4.3.1. Installing Additional Software
4.3.2. Upgrading the System
5. Packaging System: Tools and Fundamental Principles
5.1. Structure of a Binary Package
5.2. Package Meta-Information
5.2.1. Description: the control File
5.2.2. Configuration Scripts
5.2.3. Checksums, List of Configuration Files
5.3. Structure of a Source Package
5.3.1. Format
5.3.2. Usage within Debian
5.4. Manipulating Packages with dpkg
5.4.1. Installing Packages
5.4.2. Package Removal
5.4.3. Other dpkg Features
5.4.4. dpkg's Log File
5.5. Coexistence with Other Packaging Systems
6. Maintenance and Updates: The APT Tools
6.1. Filling in the sources.list File
6.1.1. Other Available Official Repositories
6.1.2. Non-Official Resources: apt-get.org and mentors.debian.net
6.2. aptitude and apt-get Commands
6.2.1. Initialization
6.2.2. Installing and Removing
6.2.3. System Upgrade
6.2.4. Configuration Options
6.2.5. Managing Package Priorities
6.2.6. Working with Several Distributions
6.3. The apt-cache Command
6.4. Frontends: aptitude, synaptic
6.4.1.  aptitude
6.4.2.  synaptic
6.5. Checking Package Authenticity
6.6. Upgrading from One Stable Distribution to the Next
6.6.1. Recommended Procedure
6.6.2. Handling Problems after an Upgrade
6.7. Keeping a System Up to Date
6.8. Automatic Upgrades
6.8.1. Configuring dpkg
6.8.2. Configuring APT
6.8.3. Configuring debconf
6.8.4. Handling Command Line Interactions
6.8.5. The Miracle Combination
6.9. Searching for Packages
7. Solving Problems and Finding Relevant Information
7.1. Documentation Sources
7.1.1. Manual Pages
7.1.2. info Documents
7.1.3. Specific Documentation
7.1.4. Websites
7.1.5. Tutorials (HOWTO)
7.2. Common Procedures
7.2.1. Configuring a Program
7.2.2. Monitoring What Daemons Are Doing
7.2.3. Asking for Help on a Mailing List
7.2.4. Reporting a Bug When a Problem Is Too Difficult
8. Basic Configuration: Network, Accounts, Printing...
8.1. Configuring the System for Another Language
8.1.1. Setting the Default Language
8.1.2. Configuring the Keyboard
8.1.3. Migrating to UTF-8
8.2. Configuring the Network
8.2.1. Ethernet Interface
8.2.2. Connecting with PPP through a PSTN Modem
8.2.3. Connecting through an ADSL Modem
8.2.4. Automatic Network Configuration for Roaming Users
8.3. Setting the Hostname and Configuring the Name Service
8.3.1. Name Resolution
8.4. User and Group Databases
8.4.1. User List: /etc/passwd
8.4.2. The Hidden and Encrypted Password File: /etc/shadow
8.4.3. Modifying an Existing Account or Password
8.4.4. Disabling an Account
8.4.5. Group List: /etc/group
8.5. Creating Accounts
8.6. Shell Environment
8.7. Printer Configuration
8.8. Configuring the Bootloader
8.8.1. Identifying the Disks
8.8.2. Configuring LILO
8.8.3. GRUB 2 Configuration
8.8.4. GRUB Legacy Configuration
8.8.5. For Macintosh Computers (PowerPC): Configuring Yaboot
8.9. Other Configurations: Time Synchronization, Logs, Sharing Access...
8.9.1. Timezone
8.9.2. Time Synchronization
8.9.3. Rotating Log Files
8.9.4. Sharing Administrator Rights
8.9.5. List of Mount Points
8.9.6. locate and updatedb
8.10. Compiling a Kernel
8.10.1. Introduction and Prerequisites
8.10.2. Getting the Sources
8.10.3. Configuring the Kernel
8.10.4. Compiling and Building the Package
8.10.5. Compiling External Modules
8.10.6. Applying a Kernel Patch
8.11. Installing a Kernel
8.11.1. Features of a Debian Kernel Package
8.11.2. Installing with dpkg
9. Unix Services
9.1. System Boot
9.2. Remote Login
9.2.1. Remote Login: telnet
9.2.2. Secure Remote Login: SSH
9.2.3. Using Remote Graphical Desktops
9.3. Managing Rights
9.4. Administration Interfaces
9.4.1. Administrating On a Web Interface: webmin
9.4.2. Configuring Packages: debconf
9.5. syslog System Events
9.5.1. Principle and Mechanism
9.5.2. The Configuration File
9.6. The inetd Super-Server
9.7. Scheduling Tasks with cron and atd
9.7.1. Format of a crontab File
9.7.2. Using the at Command
9.8. Scheduling Asynchronous Tasks: anacron
9.9. Quotas
9.10. Backup
9.10.1. Backing Up with rsync
9.10.2. Restoring Machines without Backups
9.11. Hot Plugging: hotplug
9.11.1. Introduction
9.11.2. The Naming Problem
9.11.3. How udev Works
9.11.4. A concrete example
9.12. Power Management
9.12.1. Advanced Power Management (APM)
9.12.2. Modern power savings: Advanced Configuration and Power Interface (ACPI)
9.13. Laptop Extension Cards: PCMCIA
10. Network Infrastructure
10.1. Gateway
10.2. Virtual Private Network
10.2.1. OpenVPN
10.2.2. Virtual Private Network with SSH
10.2.3. IPsec
10.2.4. PPTP
10.3. Quality of Service
10.3.1. Principle and Mechanism
10.3.2. Configuring and Implementing
10.4. Dynamic Routing
10.5. IPv6
10.6. Domain Name Servers (DNS)
10.6.1. Principle and Mechanism
10.6.2. Configuring
10.7. DHCP
10.7.1. Presentation
10.7.2. Configuring
10.7.3. DHCP and DNS
10.8. Network Diagnosis Tools
10.8.1. Local Diagnosis: netstat
10.8.2. Remote Diagnosis: nmap
10.8.3. Sniffers: tcpdump and wireshark
11. Network Services: Postfix, Apache, NFS, Samba, Squid, LDAP
11.1. Mail Server
11.1.1. Installing Postfix
11.1.2. Configuring Virtual Domains
11.1.3. Restrictions for Receiving and Sending
11.1.4. Setting Up greylisting
11.1.5. Customizing Filters Based On the Recipient
11.1.6. Integrating an Antivirus
11.1.7. Authenticated SMTP
11.2. Web Server (HTTP)
11.2.1. Installing Apache
11.2.2. Configuring Virtual Hosts
11.2.3. Common Directives
11.2.4. Log Analyzers
11.3. FTP File Server
11.4. NFS File Server
11.4.1. Securing NFS
11.4.2. NFS Server
11.4.3. NFS Client
11.5. Setting Up Windows Shares with Samba
11.5.1. Samba Server
11.5.2. Samba Client
11.6. HTTP/FTP Proxy
11.6.1. Installing
11.6.2. Configuring a Cache
11.6.3. Configuring a Filter
11.7. LDAP Directory
11.7.1. Installing
11.7.2. Filling in the Directory
11.7.3. Managing Accounts with LDAP
12. Advanced Administration
12.1. RAID and LVM
12.1.1. Software RAID
12.1.2. LVM
12.1.3. RAID or LVM?
12.2. Virtualization
12.2.1. Xen
12.2.2. LXC
12.2.3. Virtualization with KVM
12.3. Automated Installation
12.3.1. Fully Automatic Installer (FAI)
12.3.2. Preseeding Debian-Installer
12.3.3. Simple-CDD: The All-In-One Solution
12.4. Monitoring
12.4.1. Setting Up Munin
12.4.2. Setting Up Nagios
13. Workstation
13.1. Configuring the X11 Server
13.2. Customizing the Graphical Interface
13.2.1. Choosing a Display Manager
13.2.2. Choosing a Window Manager
13.2.3. Menu Management
13.3. Graphical Desktops
13.3.1. GNOME
13.3.2. KDE
13.3.3. Xfce and Others
13.4. Tools
13.4.1. Email
13.4.2. Web Browsers
13.4.3. Development
13.4.4. Collaborative Work
13.4.5. Office Suites
13.5. Emulating Windows: Wine
14. Security
14.1. Defining a Security Policy
14.2. Firewall or Packet Filtering
14.2.1. Netfilter Behavior
14.2.2. Syntax of iptables and ip6tables
14.2.3. Creating Rules
14.2.4. Installing the Rules at Each Boot
14.3. Supervision: Prevention, Detection, Deterrence
14.3.1. Monitoring Logs with logcheck
14.3.2. Monitoring Activity
14.3.3. Detecting Changes
14.3.4. Detecting Intrusion (IDS/NIDS)
14.4. Introduction to SELinux
14.4.1. Principles
14.4.2. Setting Up SELinux
14.4.3. Managing an SELinux System
14.4.4. Adapting the Rules
14.5. Other Security-Related Considerations
14.5.1. Inherent Risks of Web Applications
14.5.2. Knowing What To Expect
14.5.3. Choosing the Software Wisely
14.5.4. Managing a Machine as a Whole
14.5.5. Users Are Players
14.5.6. Physical Security
14.5.7. Legal Liability
14.6. Dealing with a Compromised Machine
14.6.1. Detecting and Seeing the Cracker's Intrusion
14.6.2. Putting the Server Off-Line
14.6.3. Keeping Everything that Could Be Used as Evidence
14.6.4. Re-installing
14.6.5. Forensic Analysis
14.6.6. Reconstituting the Attack Scenario
15. Creating a Debian Package
15.1. Rebuilding a Package from its Sources
15.1.1. Getting the Sources
15.1.2. Making Changes
15.1.3. Starting the Rebuild
15.2. Building your First Package
15.2.1. Meta-Packages or Fake Packages
15.2.2. Simple File Archive
15.3. Creating a Package Repository for APT
15.4. Becoming a Package Maintainer
15.4.1. Learning to Make Packages
15.4.2. Acceptance Process
16. Conclusion: Debian's Future
16.1. Upcoming Developments
16.2. Debian's Future
16.3. Future of this Book
A. Derivative Distributions
A.1. Census and Cooperation
A.2. Ubuntu
A.3. Knoppix
A.4. Linux Mint
A.5. SimplyMEPIS
A.6. Aptosid (Formerly Sidux)
A.7. Damn Small Linux
A.8. And Many More
B. Short Remedial Course
B.1. Shell and Basic Commands
B.1.1. Browsing the Directory Tree and Managing Files
B.1.2. Displaying and Modifying Text Files
B.1.3. Searching for Files and within Files
B.1.4. Managing Processes
B.1.5. System Information: Memory, Disk Space, Identity
B.2. Organization of the Filesystem Hierarchy
B.2.1. The Root Directory
B.2.2. The User's Home Directory
B.3. Inner Workings of a Computer: the Different Layers Involved
B.3.1. The Deepest Layer: the Hardware
B.3.2. The Starter: the BIOS
B.3.3. The Kernel
B.3.4. The User Space
B.4. Some Tasks Handled by the Kernel
B.4.1. Driving the Hardware
B.4.2. Filesystems
B.4.3. Shared Functions
B.4.4. Managing Processes
B.4.5. Rights Management
B.5. The User Space
B.5.1. Process
B.5.2. Daemons
B.5.3. Inter-Process Communications
B.5.4. Libraries

---

