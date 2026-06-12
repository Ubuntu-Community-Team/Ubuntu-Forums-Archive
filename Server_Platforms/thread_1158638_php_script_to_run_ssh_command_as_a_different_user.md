---
title: "php script to run ssh command as a different user"
date: 2009-05-13
forum: Server Platforms
---

### Post by orange-wedge on 2009-05-13
This post may be out of the scope for help on this forum, but I'll give it a shot.  I've got an ubuntu web server running drupal and mysql, so I all the php code has to be executable by the user drupal-cron.  I have three other servers that I maintain certain statistics through remote ssh commands, and update them to the mysql DB that is used for the drupal site.  These statistics are updated once a day using a cron as a different user than drupal-cron, and I have created an rsa-key for that user to provide passwordless entry to other three servers.

I want to add a realtime script (link on the site) to update the information about the three servers, thus I need to run the ssh commands as a different user than drupal-cron.

Does anyone know of a good method to do this?

I was entertaining two ideas:

[LIST]
[*]To setup a cron for the ssh user to check for a flag from the php script every minute (This isn't exactly realtime but it is close.)
[*]To have a daemon process run by the ssh user to check for a flag from the php script periodically, possibly every second (My only concern with this is monitoring the daemon and making sure it does not die.  I have already installed daemontools in anticipation of setting up a script like this.)
[/LIST]
Thanks in advance.

---

### Post by a9k3d on 2009-05-14
Possibilities:
1) Why not run it directly from php or cron. Pass the rsa key in the ssh command with -i <identity>. SSH defaults to using the identity in ~/.ssh but -i can override that.
2) Not sure of this one but I think I did something like it 3 years ago:
a) create a script with sudo -u <ssh-user> <ssh commands to get stuff>
b) add the cron or php user to /etc/sudoers is explicit permission to run just the above script.

---

