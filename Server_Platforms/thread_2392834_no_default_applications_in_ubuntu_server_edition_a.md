---
title: "no default applications in ubuntu server edition and no repo"
date: 2018-05-26
forum: Server Platforms
---

### Post by shayanthethief on 2018-05-26
Hi, I recently bought a VPS for cheap from "germanvps.com" and rebuilded the server with ubuntu 14.04. there is no - nano, gedit, ...- installed by default on it and when I try to install them with "apt-get install nano, ..." it says either unable to locate package  or
packagex doesn't have an installation candidate.

---

### Post by PaulW2U on 2018-05-26
> **shayanthethief said:**
> Hi, I recently bought a VPS for cheap from "germanvps.com" and rebuilded the server with ubuntu 14.04. there is no - nano, gedit, ...- installed by default on it and when I try to install them with "apt-get install nano, ..." it says either unable to locate package  or
packagex doesn't have an installation candidate.
I have Ubuntu Server 14.04.5 running in Virtualbox and nano is installed by default. gedit is installable although it brings in nearly 200 dependencies.

I have used three VPS providers in the past and I've not always seen something that looks and feels like Ubuntu. I wonder how much customisation is performed on the initial installation by your provider?

Can you install any new software?

What is the output of 
```
cat /etc/apt/sources.list
```
In that output you should be seeing lines that refer to trusty, trusty-backports, trusty-security and trusty-updates.

What does your provider have to say about your issue?

---

### Post by TheFu on 2018-05-26
> **shayanthethief said:**
> Hi, I recently bought a VPS for cheap from "germanvps.com" and rebuilded the server with ubuntu 14.04. there is no - nano, gedit, ...- installed by default on it and when I try to install them with "apt-get install nano, ..." it says either unable to locate package  or
packagex doesn't have an installation candidate.

If I ran a VPS provider, I'd deploy the minimal server image possible.  I certainly wouldn't install any GUI tools like gedit.  Linux servers don't have a GUI and you'll be disappointed trying to run remote X11.   Personally, I purge nano from all my systems so vim becomes the default system editor.  But which editor you want is your business.

As for installing packages, run **sudo apt-get update**  and fix any issues with that first.  Then run **sudo apt-get upgrade** to ensure everything is currently patched.  After that, assuming there aren't any problems, install nano.

If the 'update' fails, try to use a web browser to access the locations that the server is failing on.  Does that work or not?  Could just be a DNS config issue.

---

### Post by SeijiSensei on 2018-05-27
I'll just say that nano with its menus is much better suited for inexperienced users.  I use the jed clone of emacs myself.  I've always found vim too opaque, though emacs is hardly obvious!  Nano was written at the University of Washington as part of its Pine e-mail system.  It was designed in the days of text-mode computing so that thousands of students, faculty, and staff could send email easily.  (One lasting legacy of that project is the IMAP protocol.)

OP, did you first run "sudo apt update" before trying to install packages?  Run that and see if you get errors.  Did Ubuntu find all its repositories and update its package lists?

If you want to run *nix servers, you need to get used to the command prompt.  That's especially true for managing remote servers at provider sites.  If you need a server with a GUI, lease a Winoows Server, though it'll cost more than a Linux instance.  [https://azure.microsoft.com/en-us/pricing/](https://azure.microsoft.com/en-us/pricing/)

---

