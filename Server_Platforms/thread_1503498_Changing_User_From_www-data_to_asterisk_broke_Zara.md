---
title: "Changing User From www-data to asterisk broke Zarafa."
date: 2010-06-06
forum: Server Platforms
---

### Post by GraysonPeddie on 2010-06-06
Hi, y'all. I currently have [Zarafa](http://www.zarafa.com/) and I am going to install MythWeb for MythTV.

To solve the permission problem for installing amportal (FreePBX), I have to change Apache's user and group to Asterisk instead of this, which I've commented out:

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

Once FreePBX is installed completely, I checked to make sure FreePBX is working and it worked. I used the latest version of Asterisk from the SVN trunk, so I used ./install_amp --my-svn-is-correct.

However, I want to use Zarafa AND FreePBX, I just don't like having to change the Apache User and Group to asterisk.

Here is a couple of examples of instructions when installing FreePBX:

[http://ubuntuforums.org/showthread.php?p=8924897](http://ubuntuforums.org/showthread.php?p=8924897)
[http://www.voip-info.org/wiki/view/How+to+install+Asterisk+1.4+and+FreePBX+2.3.1+in+Ubuntu+Linux](http://www.voip-info.org/wiki/view/How+to+install+Asterisk+1.4+and+FreePBX+2.3.1+in+Ubuntu+Linux)

Is there a workaround? I really want to change it back to what it was before while FreePBX can still access their own directories.

I did not know if this question has been asked, but I thought I'd ask here. I've added "zarafa" and "mythweb" to the tags list my thread.

Update: I changed my apache configuration file back to www-data for User and Group and I do have /var/lib/asterisk/agi-bin and /var/www/asterisk (where FreePBX PHP pages are installed in /var/www/asterisk) owned by asterisk:asterisk. But I get this:

```
Retrieve conf failed to copy file(s) from a module's agi-bin dir: copy(/var/lib/asterisk/agi-bin/directory): failed to open stream: Permission denied
copy(/var/lib/asterisk/agi-bin/sql.php): failed to open stream: Permission denied
copy(/var/lib/asterisk/agi-bin/checksound.agi): failed to open stream: Permission denied
copy(/var/lib/asterisk/agi-bin/dialparties.agi): failed to open stream: Permission denied
copy(/var/lib/asterisk/agi-bin/fixlocalprefix): failed to open stream: Permission denied
copy(/var/lib/asterisk/agi-bin/list-item-remove.php): failed to open stream: Permission denied
copy(/var/lib/asterisk/agi-bin/enumlookup.agi): failed to open stream: Permission denied
copy(/var/lib/asterisk/agi-bin/user_login_out.agi): failed to open stream: Permission denied
```

What changes do I need to make in order for FreePBX to work?

In short, Zarafa webaccess works, but FreePBX does not work.

I don't like to do this, but I'm thinking that my last, and only choice, is to change ownership for /var/www/webaccess to asterisk:asterisk, but that is an alias for /usr/share/zarafa-webaccess and I don't want to mess with their ownership and permissions to make it part of asterisk:asterisk.

---

### Post by GraysonPeddie on 2010-06-08
For those who read this, I just got rid of [Zarafa](http://www.zarafa.com/). Zarafa Migration Tool does not work with Microsoft Outlook 2007 when I exported as a PST file and I'm having trouble connecting to Zarafa Community Edition (including 3 users Outlook support). I did have my user assigned as admin rights, but I can only connect to Zarafa through webaccess. I've been trying to migrate from Hosted Exchange (Sherweb) to Zarafa (in-house).

I tried Zimbra, but when I see the "starting servers" when installing Zimbra, it took me a very long time for me to wait and I kind of went like "something is wrong," so I restarted my Ubuntu server and it got hosed. I've selected [Debian 5, 64-Bit (amd64)](http://www.zimbra.com/downloads/os-downloads.html) since there's no official support for Ubuntu 10.04.

So, I'm completely out of luck with Zaarafa (I do get mixed up with spelling out "Zarafa" with "Zafara." Who came up with that name? Geez... :|) and Zimbra, so I'm sticking with Hosted Exchange for now (I like to have a couple of features of Microsoft Exchange -- I don't care if Microsoft Exchange is overkill or not; besides, I'm a hobbyist :)).

I realized that I changed my subject completely in my thread. So anyway, with getting FreePBX to work when I set my Apache environment variables to www-data for User and Group, I'd like to say "never mind," as I'll just have to let "asterisk" (err, FreePBX) have exclusive access to Apache, as MythWeb for MythTV does not require write access. Or does it? I don't know... I might be better off having a separate virtual machine and have MythWeb connect to MythTV in a "non-virtual" machine (what I mean is if MythWeb has an IP address of 10.0.0.5 and MythTV server has an IP address of 10.0.0.1, I just configure Apache to have MythWeb connect to 10.0.0.1).

My only problem left is getting FreePBX fixed up after my installation of MythWeb. When I went to yourdomain.com/asterisk (where FreePBX gets installed in), I get a web page with "Index of /asterisk" which then I'll have to click index.html. Click in "FreePBX Administration" and that will take me to "Index of /asterisk/admin" and I click in "index.php." It is embarrassing to and I don't know how I can fix this to get it to work like it was before I install MythWeb. The installer did ask me if I want to use MythWeb exclusively with the Apache web server and I said "no."

---

