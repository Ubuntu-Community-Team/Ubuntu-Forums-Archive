---
title: "Another security question"
date: 2013-03-26
forum: Security
---

### Post by cheatos on 2013-03-26
Hi all,

I am not really worried about my OS security. I have been using ubuntu (or lubuntu) for about 2 years now and ran a clamav scan on my machine recently with no found viruses or stuff...

However I am interested in these security issues of flash and other multi-platform programs. How do viruses coming via flash "work"? Will they also be able to infect my Linux system or are they just some sort of backdoor to make malicious code executable on windows machines?

Thanks for your answers!

---

### Post by ManamiVixen on 2013-03-26
You don't need a virus scanner for linux. Clam AV is for scanning files for Windows viruses on a linux box before they are sent to a Windows PC. As for Flash exploits, they cannot harm your linux PC beyond screwing your Home folder. So there is a possibility of danger, but it isn't too big. You are pretty safe. Best advice, never enter your password for root access for a window that pops out the blue asking for it.

---

### Post by Cheesemill on 2013-03-26
Take a read of the wiki, it should explain the basics of computer security to you...

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by cheatos on 2013-03-26
k, thanks for your help.
I have read, that there have already been some viruses for linux, so what do you mean by
> Clam AV is for scanning files for Windows viruses on a linux box before  they are sent to a Windows PC. As for Flash exploits, they cannot harm  your linux PC beyond screwing your Home folder.
How may my home folder be screwed?

---

### Post by ManamiVixen on 2013-03-26
The home folder is the only folder that dosen't require a password to access it's contents. So anybody can technically access it. But the chances of somebody messing with it really are slim.

---

### Post by wildmanne39 on 2013-03-26
*Thread moved to **Security Discussions**.*

---

### Post by Hungry Man on 2013-03-26
You visit malicious webpage.

Attacker compromises FlashPlayer.

Attacker now controls FlashPlayer process.

Attacker can now access anything FlashPlayer can access.

At this point you want to restrict what FlashPlayer can access with Apparmor. Run your browser in a profile.

---

### Post by SeijiSensei on 2013-03-27
> **ManamiVixen said:**
> The home folder is the only folder that dosen't require a password to access it's contents. So anybody can technically access it. But the chances of somebody messing with it really are slim.

Canonical has chosen to make /home/username have 755 permissions by default in Ubuntu.  That means users can list and read each others' files.  This is a controversial decision, and one I do not support. I prefer the RedHat default where /home/username has 700 permissions.  You can change the default permissions in /etc/adduser.conf to make this the default for Ubuntu as well.  On a multi-user system with well-specified user groups, you might want 750 permissions to allow other group members to view your files but deny everyone else.

---

### Post by cheatos on 2013-03-27
ok, so in response to Hungry Man
How do I make my browser run in a specific profile?

Furthermore, i only have one user on my system at the moment, so changing the permissions to 700 would be rather pointless, right?

---

