---
title: "Upgrade Worries"
date: 2014-09-26
forum: Server Platforms
---

### Post by suprleg on 2014-09-26
I have a remote "Folding@Home Server" running Ubuntu 12.04.5 LTS. This server has numerous scripts running in the background used for various start-up and reporting functions that make everything "auto-magically" work with little effort. Recently when I log into this box I'm asked to upgrade to Ubuntu 14.04.1 LTS.
I'm worried that upgrading will either not work correctly, as documented in numerous places over that last months, or work, but mess-up the scripting rendering the server inoperable.
So my question would be: is it necessary to complete this OS upgrade as long as I continue to patch/update the Ubuntu 12.04.5 install?
It should be noted that I'm an Operator for a F@H club and this machine is in my care and not owned by myself personally. 
Thanks

---

### Post by Vladlenin5000 on 2014-09-26
Ubuntu 12.04 is supported until 2017 therefore you can keep it as long as the support goes. Upgrading a production server isn't always the best course of action.

---

### Post by deadflowr on 2014-09-26
+1 to post #2.

Also, is this a server or a desktop install with server packages installed?

If a desktop, then open the update manager, go to Settings, click to open.
Then go to the Updates tab and find the line for notify for new release, and change to never.

If it is a barebone server, without a gui(command line only) you need to edit the file
/etc/update-manager/release-upgrades
change the line from Prompt=lts to Prompt=never.

Both methods will stop the upgrade message from appearing.

Just remember that support ends in april 2017.

---

### Post by slickymaster on 2014-09-26
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Bashing-om on 2014-09-26
suprleg; Hey, Me too !

^^ If this is a working server -> if it ain't broke, Don't fix it !

[INDENT][INDENT]newer may not be better
[/INDENT][/INDENT]

---

### Post by suprleg on 2014-10-03
Thanks for the responses. It looks like most, including myself, are in agreement with the "if it ain't broke don't fix it" theory. 
For now or until some serious problem arises this solution will suffice and I'll continue to update my existing installation.

---

### Post by DigiAngel on 2014-10-05
I would have to wholeheartedly agree.  My upgrade from 12 to 14 was a complete disaster...so much so that I went back to 12.  Things that were broken:

Dovecot/postfix (additional config lines or fails to start, mail_dir a mystery, mailbox_command vanished)
Apache directory change (/var/www now has to go to /var/www/html)
Apache needed "sudo phpenmod mcrypt" in order to start
OpenSwan competely broken (xl2tpd fails to respond) - I did see in the release notes that strongSwan is now "fully supported", but I didn't expect it to blow up OpenSwan
That "talloc memory leaking" constantly showing up in syslog

To be honest it was a joke...my current 12 setup runs perfect...an upgrade just shouldn't destroy functionality.  I upgraded from 10 to 12 with only a few minor issues, but 12 to 14 just didn't seem to be vetted.  I know when I do go to 14, it will be a redo on a seperate machine then port over...NEVER again will I do an in place upgrade.

---

