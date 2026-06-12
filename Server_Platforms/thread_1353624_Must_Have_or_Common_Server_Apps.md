---
title: "Must Have or Common Server Apps"
date: 2009-12-13
forum: Server Platforms
---

### Post by spikoley on 2009-12-13
I am setting up server as an educational experience.  What common apps do most people use?  What do you recommend?

---

### Post by fancypiper on 2009-12-13
LAMP, of course.
# Install web server packages
sudo tasksel install lamp-server

---

### Post by spikoley on 2009-12-13
> **fancypiper said:**
> LAMP, of course.
# Install web server packages
sudo tasksel install lamp-server

Thanks for the reply.  I already set up LAMP with vhosts.  I am looking for other standard server projects.  Any other ideas on what to set up?

---

### Post by HighCommander540 on 2009-12-13
> **spikoley said:**
> Thanks for the reply.  I already set up LAMP with vhosts.  I am looking for other standard server projects.  Any other ideas on what to set up?

Yeah, actually if you just issue the "sudo tasksel" command. It will show you all of the standard server packages that Ubuntu offers. Like e-mail or DNS. If you still think you need other stuff, just post.

---

### Post by Lars Noodén on 2009-12-13
What are the "must do" classroom activities?  That will determine which apps you want to look at.

Streaming live audio or video would be one option.  You could broadcast, either audio or video, live school concerts, plays, sporting events or other performances.  For those, look at vlc, ffmpeg and icecast2

Programming and software or systems development would mean installing git, bazar or svn.  

etc.

---

### Post by craigp84 on 2009-12-13
A random list of things to have good hands on experience of:

System Configuration:

Design & implement a backup regime
Test bare metal restore
Managing configuration changes (generally boils down to - put /etc under version control in small deployments) 
Design & document user / group ID ranges & allocations for your network
Setup user management scripts
Setup system monitoring tools (sar / sysstat, monit, munin - include hardware monitoring (SMART HDDs, temperatures, case intrusion switches where present etc.)
Setup ulimits for untrusted user classes (prevent users killing the box with rogue / runaway processes)
Refine sysctl configuration
Configure syslog
Setup audit


Network services:

SSH
DNS
DHCP
Firewall
Mailserver
Kerberos
Windows integration (Active Directory)
Web proxy (bonus points for a management interface to view what employees are browsing, i like "Squint")
Intranet website (wiki, discussion forums, news / blog, phonebook, dropbox etc.)

These are just things i'd be familiar with if you're looking to go into a sysadmin role later in life. The sky is the limit with ideas (virtualisation is a key one nowadays) but these hopefully get you started.

---

