---
title: "Web server user and sudo permissions"
date: 2008-07-15
forum: Server Platforms
---

### Post by cldfzn on 2008-07-15
I am trying to configure a web server to be able to call certain commands as an elevated permissions user.  The problem I am running into is i need to ssh to another server and run a command on that machine all as the elevated user.  I only want certain commands to be able to be processed but the user needs to be able to specify part of the command, say a cat <file> | grep <wildcards>.  I want to do this but every way I have been able to think of, only opens a possible security hole.
What are some of your suggestions?

---

### Post by cdenley on 2008-07-15
When you specify a command in your sudoers file, you permit any command starting with that string. For example, if you allow "/bin/grep", they can also run "/bin/grep anything". Also, when you pipe command output to files or other commands with "|" the commands are processed separately. That means "sudo cat <file> | grep <wildcards>" will run cat as root, but grep the output of the cat command as the original user.

The best way I could think of would be to ssh into the server with public key authentication (so you don't need a password) as a restricted user like www-data, then use sudo for commands that need root. Use visudo to configure your sudoers file to allow www-data to run your specific commands as root without a password.

Any solution you come up with is going to open up more possibilities for malicious users. This probably isn't a good idea. Be very careful.

---

### Post by cldfzn on 2008-07-15
Yea, those are pretty much my thoughts exactly.  Only I don't have control over the setup, I'm just tasked with trying to find some solution that is secure :rolleyes:.  Is there a way to have a user only allowed to sudo commands contained in a single perl script.  My idea is that if the execution of my script is allowed to run the commands as the network script user then I can whitelist commands to be used and blacklist every thing else, something I haven't found possible with sudoers.  We're basically trying to poll logs from external servers and create a lovely web interface to do so.

---

### Post by cdenley on 2008-07-15
> **cldfzn said:**
> Yea, those are pretty much my thoughts exactly.  Only I don't have control over the setup, I'm just tasked with trying to find some solution that is secure :rolleyes:.  Is there a way to have a user only allowed to sudo commands contained in a single perl script.  My idea is that if the execution of my script is allowed to run the commands as the network script user then I can whitelist commands to be used and blacklist every thing else, something I haven't found possible with sudoers.  We're basically trying to poll logs from external servers and create a lovely web interface to do so.

It would probably be easier to just allow the script user to sudo your script. You can make specific rules in your sudoers file for specific commands.
```
scriptuser ALL=NOPASSWD:/path/to/myscript
```
Or maybe you can set the script user's shell to your script, so when you log in, it runs your script then exits.

If you're really concerned about security, you can chroot the script user, then create links to the directories the script user needs access to.

---

### Post by cldfzn on 2008-07-15
The return has to come to the webpage.  i.e. www-data needs to elevate permissions to ssh to an external box, poll some logs with varying wildcards delivered to cat/grep/awk.  Then the output of the cat/grep/awk must be returned to the web interface.  All without opening security holes and they'd prefer to not have a login for the web interface...

and btw thanks ;D

---

### Post by windependence on 2008-07-16
> **cldfzn said:**
> Yea, those are pretty much my thoughts exactly.  Only I don't have control over the setup, I'm just tasked with trying to find some solution that is secure :rolleyes:.  Is there a way to have a user only allowed to sudo commands contained in a single perl script.  My idea is that if the execution of my script is allowed to run the commands as the network script user then I can whitelist commands to be used and blacklist every thing else, something I haven't found possible with sudoers.  We're basically trying to poll logs from external servers and create a lovely web interface to do so.

Why reinvent the wheel here? There are quite a few free open source apps that can do this nicely already. Cacti and Nagios come to mind but there are plenty more.

The other way to do this would be to have a dedicated user pull the logs to your server and then have the results displayed by Apache. That way you would not have to elevate permissions for the Apache user.

-Tim

---

### Post by cldfzn on 2008-07-16
Well, we're running nagios, but we're not polling logs in the same manner.  We need more indepth and specific polling of the logs looking for specific sessions.  Pulling the logs back is not something that will be done currently, the logs are huge and numerous.

---

