---
title: "Errors re-configuring Bastille"
date: 2011-05-21
forum: Security
---

### Post by silver_roxy_79 on 2011-05-21
I recently installed Bastille as one of several programs to protect my new install. When I was going through the configuration, I was under the impression selecting to disable single user login would still allow me to login using my root password. On the graphical login screen it does not work.
 
When I boot in recovery mode (I had a dual-boot installed), I can login in fine, but this is in a command line/terminal like screen. I attempted to re-configure Bastille using this screen, and here are my lackluster results.
 
Command:
/usr/sbin/InteractiveBastille -c
 
This command takes me through the questioning phase, but at the end I receive this error message when trying to save the new configuration.
 
Failed to open log file /var/log/Bastille/action-log: Permission Denied
and 
ERROR: couldn't not write to etc/Bastille/config (exact wording!)
 
I am not sure how to remedy this. I am tempted to try to uninstall Bastille and try something else, but I do want to have a security package as I file share.
 
I am new to the Linux command line system, so please over-explain any solutions.

---

### Post by bodhi.zazen on 2011-05-21
You probably need to run that command with sudo.

```
sudo /usr/sbin/InteractiveBastille -c
```

Also if you are new to LInux you should probably do some reading before you use such a tool as the options are quite generic and not specific to Ubuntu. If you are new you likely will not know how to properly configure it.

I would start with the security stickies.

---

### Post by Soul-Sing on 2011-05-21
you can reset all bastille "rules", it is the faq.
If you're not happy with the changes Bastille makes to your computer, you can run bastille -r to reverse its changes

---

### Post by silver_roxy_79 on 2011-05-21
Thanks for your help guys.

I entered /usr/sbin/RevertBastille into the command line and it undid everything. Then I promptly unintalled it. I'll just have to look for something else.

---

