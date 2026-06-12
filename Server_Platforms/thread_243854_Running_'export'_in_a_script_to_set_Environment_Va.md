---
title: "Running 'export' in a script to set Environment Variables doesn't Stick"
date: 2006-08-25
forum: Server Platforms
---

### Post by Avian00 on 2006-08-25
Hi,

I'm trying to run a script which executes a series of 'export' commands to set environment variables (It is the vars script from openvpn, if that helps).  For some reason, the variables that get set during the script do not stick after the script has been run.  If I 'echo' those variables while the script is running, they appear to be set, but once the script ends, those variables are no longer set.  If I set the variables from the command line manually, they DO stick.  How can I make these variables remain after the script ends?

Thanks in advance for any help.

Matt

---

### Post by chonger on 2006-08-25
Try "sourcing" that file instead of running it as a script.

In bash, either do
```

$ source file-with-variables
# or
$ . file-with-variables
```

---

### Post by Avian00 on 2006-08-25
Thanks!  That did it!  I should have read the instructions a little more closely.  I thought that they had typoed and left out the '/' on the '. file-with-variables' instructions

---

