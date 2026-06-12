---
title: "[SOLVED] Automatic updates"
date: 2008-05-03
forum: Security
---

### Post by Tantor on 2008-05-03
Hi. At work, we have some computers that we share. We don't work in front of the computers but have them on all day and use them now and then to look something up, write emails, print stuff, etc. I recently installed Ubuntu in one of them, the others run WinXP. Everything is working fine, but I have one security concern.

We have a slow internet connection, so when I download software/updates with synaptics it can take some hours. I normally start the download process and go to do something else (outside the computers room). My concern is that I have to leave my user acount open, so anyone that walks in has access to my terminal. Is there some way to tell the SO to "do this and log me off when you are done; in the meantime do not accept any other command". At least, is there a way to automatically download and install the updates (say at night) without having to log in (I know that the Windows machines do that).

Thanks in advance!

---

### Post by brian_p on 2008-05-03
> **Tantor said:**
> We have a slow internet connection, so when I download software/updates with synaptics it can take some hours. I normally start the download process and go to do something else (outside the computers room). My concern is that I have to leave my user acount open, so anyone that walks in has access to my terminal. Is there some way to tell the SO to "do this and log me off when you are done; in the meantime do not accept any other command". At least, is there a way to automatically download and install the updates (say at night) without having to log in (I know that the Windows machines do that).

Thanks in advance!

Run a cron job using apt-get or aptitude. Lock the screen to prohibit access.

---

### Post by mrzaius on 2008-05-03
To clarify, if necessary, use the following guide to add an entry in the cron scheduler's configuration file that will run "apt-get update" and "apt-get dist-upgrade -y" [http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm](http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm)

Also, if you end up with enough machines that that becomes impractical, use the following guide (or something like it) to make one of those hosts become a local Ubuntu mirror, so that you only end up downloading the packages once. Of course, funneling apt across a properly configured HTTP proxy will have a similar end result.

---

### Post by RAOF on 2008-05-05
System->Administration->Software Sources has some 'automatic updates' options; you can set it to automatically install security updates or automatically download updates in the background.

You can also use the "Switch User" functionality to lock your session and allow others to log in.

---

### Post by Tantor on 2008-05-12
Thanks, this "cron job" thing was what I was looking for. Thanks also for the quick guide!

---

