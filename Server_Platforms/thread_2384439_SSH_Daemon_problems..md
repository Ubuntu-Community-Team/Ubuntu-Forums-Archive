---
title: "SSH Daemon problems."
date: 2018-02-07
forum: Server Platforms
---

### Post by liutauras on 2018-02-07
[FONT=arial, helvetica, sans-serif][COLOR=#333333]I have been following this guide, to secure my ubuntu [/COLOR][/FONT]ubuntu 16.04 lts server, but I ran in into some problems, now I need help because I don't understand how to solve it, and if you can help me please give me all the scrips because Im very new.

So I have tried editing my [COLOR=#000000][FONT=Monaco]/etc/ssh/sshd_config [/FONT][/COLOR] file and this happened. I changed these lines just like the guide said:

# Authentication:
...
PermitRootLogin no



# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

And added this to the end of the sshd_config.

echo 'AddressFamily inet' | sudo tee -a /etc/ssh/sshd_config

Then I tried to [COLOR=#333333][FONT=Helvetica]Restart the SSH service to load the new configuration. [/FONT][/COLOR][COLOR=#333333][FONT=Monaco, Menlo, Consolas, Courier New, monospace] With this command:

[/FONT][/COLOR]sudo systemctl restart sshdI got the error: [COLOR=#333333][FONT=arial] I get Job for ssh.service failed because the control process exited with error code. See "systemctl status ssh.service" and "j[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]ournalctl -xe" for details.
[/FONT][/COLOR]
Then my server support told me to type this command and check of there is any typos in the sshd_config:

[COLOR=#333333][FONT=arial]sudo /usr/sbin/sshd -t

[/FONT][/COLOR]And there was a typo in the last line so I deleted this line that was told to add in the guide:

echo 'AddressFamily inet' | sudo tee -a /etc/ssh/sshd_config
Now Whenever I try command sudo [COLOR=#333333][FONT=arial]systemctl restart sshd [/FONT][/COLOR] , I get [COLOR=#333333][FONT=arial]sudo: unable to resolve host.[/FONT][/COLOR],  [COLOR=#333333][FONT=arial]If I use the command systemctl restart sshd (without sudo) I get:


[/FONT][/COLOR][COLOR=#333333][FONT=arial]Failed to restart sshd.service: The name org.freedesktop.PolicyKit1 was not provided by any .service files[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]See system logs and 'systemctl status sshd.service' for details.

[/FONT][/COLOR][COLOR=#333333][FONT=arial]If I try: /usr/sbin/sshd -t (without sudo) It says: 

Could not load host key: /etc/ssh/ssh_host_rsa_key[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Could not load host key: /etc/ssh/ssh_host_dsa_key[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Could not load host key: /etc/ssh/ssh_host_ecdsa_key[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Could not load host key: /etc/ssh/ssh_host_ed25519_key[/FONT][/COLOR][COLOR=#333333][FONT=arial]
[/FONT][/COLOR]
At this point I'm totally lost, If you know how to fix this please help.

---

### Post by howefield on 2018-02-07
Thread moved to the "*Server Platforms*" forum.

---

### Post by steeldriver on 2018-02-07
It sounds like your problem is with sudo (an/or the /etc/hosts or /etc/hostname files), rather then with the (now corrected) /etc/ssh/sshd_config file - see for example [Error message 'sudo: unable to resolve host <USER>']("https://askubuntu.com/questions/59458/error-message-sudo-unable-to-resolve-host-user")

HTH

---

