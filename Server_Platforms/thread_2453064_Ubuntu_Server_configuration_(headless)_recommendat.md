---
title: "Ubuntu Server configuration (headless) recommendations:"
date: 2020-11-02
forum: Server Platforms
---

### Post by gomie on 2020-11-02
[FONT=Arial]We have previously used hosted solutions, but have become frugal due to the current pandemic. Hence, we decided to go for our own server (run on a 6 year old Dell desktop with sufficient specs) for test and trials, based on Ubuntu Server 20.04 LTS, or earlier release if so recommended by the forum – stability matters.[/FONT]
 
 
 [FONT=Arial]Long story short, what we don’t want are to install unnecessary applications/packages running, consuming both processing power and opening up ports for security issues. We are users of Ubuntu Desktop, so we are familiar with the basics, but lack the skills to set up a server.[/FONT]

 
 
 [FONT=Arial]There are an abundance of applications and services available in the package, but as mentioned above, we need to keep it to a strictly necessary level.[/FONT]
 
 
 [FONT=Arial]What we intend to use the server for is essentially:[/FONT]
 
 
 [FONT=Arial]- Host/Run/Access a database (PostgreSQL, MySQL or MariaDB)[/FONT]
 [FONT=Arial]- Access/Sync remote databases through API/Query[/FONT]
 [FONT=Arial]- File storage (File Server)[/FONT]

 [FONT=Arial]- Backup of system and content[/FONT]

 [FONT=Arial]- Security service/server/functionality (FOSS)[/FONT]
 [FONT=Arial]- Remote management server (WebGUI) (FOSS)[/FONT]
 [FONT=Arial]- Remote management database, if not bundled (FOSS)[/FONT]
 [FONT=Arial]- System update/upgrade[/FONT]
 
 
 [FONT=Arial]The server will be connected to a router (DMZ) behind a firewall, but also accessed from LAN, and only needed ports will be opened in the fw.[/FONT]
 
 
 [FONT=Arial]Security and integrity is a major concern, and we need to access the server securely, with logs.[/FONT]
 
 
 [FONT=Arial]Would really appreciate your help, guidance and assistance. What are your recommendations?[/FONT]

 
 
 [FONT=Arial]Thanks in advance[/FONT]

---

### Post by LHammonds on 2020-11-02
You are wanting a single server to do all of this AND sit on your DMZ and be bridged with direct access to your LAN?

If so, it does not sound secure at all.

A DMZ is where you put things like a web server that has zero connectivity to your LAN (in the event of it getting compromised and used as an attack vector.  It is not where you plug something in to bypass the firewall and have access to your LAN.

If you are going to have a backup, it needs to exist where the machine itself cannot access it (again, if the machine is compromised, any backups it can see/touch is also compromised).

It is hard to do all of this with a single server...even if you put a hypervisor on it such as ESXi, KVM or Proxmox...you still need separate storage for backup for at least the basic 3-2-1 backup rule (3 backups on at least 2 different mediums and 1 being offsite).

LHammonds

---

### Post by gomie on 2020-11-03
Thanks for your comment.

If you do not recommend connection to DMZ, how do we make the server accessible regardless of whether we are on LAN or WAN?

Your remarks about backup...noted. We will use drives offsite.

Any suggestions on what packages are a necessary on the server - minimum?

---

### Post by mastablasta on 2020-11-05
> **gomie said:**
> 
Any suggestions on what packages are a necessary on the server - minimum?

by default it will install only necessary packages. you then get the option to install additional ones before the install ends or you can do that later on.

the more packages you add the bigger the area of attack get's and you need to compensate that with proper hardening.

For example WebGUI for servers is good to have (not that you really need it), but it brings with it additional attack options.

my suggestion - if you have virtualbox try a few server centered distros and apps. you can try the individual applications using their preinstalled images: [https://bitnami.com/stacks](https://bitnami.com/stacks)
Check Zentyal - Ubuntu based Small Business Server.
If this is going to be a kind of NAS server then OpenMediaVault is Debian based server with WebGUI configuration
Nethserver is similar one but CentOS based.

For Ubuntu server GUI i use Ajenti - it's light and python based. it has text editor, CLI, dashboard, you can turn stuff on or off with a click. I still use version 1.x
i also use LAMP, PHPMyAdmin, Nextcloud, OpenSSH for secure remote connection to server, fail2ban and some others to harden it a bit.

If this will be file exchange server, for collaboration work then Nextcloud is a popular platform. and has a GUI.

backup - will it be push (to server) or pull (from server)? is the server the one doing backup or you mean backup of server?

---

