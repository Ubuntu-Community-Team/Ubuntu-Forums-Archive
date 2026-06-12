---
title: "Need help with script using ssh &amp; sshpass to connect local computers."
date: 2018-09-24
forum: Server Platforms
---

### Post by coredumped2 on 2018-09-24
I am attempting to run a script to open terminals for my local machine  and 3 locally networked computers. I want to double-click the script file on the desktop to run it, I want to have the password input in  the script, I want root access, and I want to change the directory in  each terminal. Currently, my script is able to open a terminal with root  access for each computer, but the local one closes for some reason.  Also, I cannot seem to find the script command in order to change  directories, as my attempts to append a "cd /home/somedirectory/"  command have failed. Here is my code:

```
#!/bin/bash
gnome-terminal -x bash -c "sudo -S < <(echo "password") cd /home/somedirectory"
allcomputers=(computer1 computer2 computer3 computer4)
for currentcomputer in ${allcomputers[@]};
do
  if [ $currentcomputer != $HOSTNAME ]
  then
      gnome-terminal -x bash -c "sshpass -p password ssh root@$currentcomputer"
  fi
done
```

I  am new to Linux and have pieced this together from what I found online,  so I may have missed a very simple command. Any help is greatly  appreciated.

---

### Post by SeijiSensei on 2018-09-24
First, read up on using "shared keys" in SSH.  Then you won't need to use a password to connect.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by coredumped2 on 2018-09-25
Thank you for letting me know about that and including a link.

While  I will definitely try that way for my own personal computers, the  project I am working on requires that I perform the task how I described  it in my question. Sorry, I should have specified that earlier.

---

### Post by TheFu on 2018-09-27
Sorry, but the question is flawed and shows a lack of understanding for Unix security, IMHO.

SeijiSensei was being kind by suggesting the use of ssh-keys for authentication.  Using passwords is actually considered a security failure these days.

Remote root is also considered dangerous, even with ssh-keys. In ubuntu, the root account isn't enabled. Users are expected to login using a different account and use sudo to elevate permissions as needed, if the account has that privilege.

We aren't allowed to explain how to enable root use directly in these forums.  

To access multiple computers, there are a number of existing solutions.  
* ClusterSSH - this doesn't scale much over the available screen space.
* Expect - this is extremely old-school and based on Tk/TCL.
* Any of the DevOps tools like Ansible, Puppet, Chef, SaltStack, Rex and a few other minor tools.

But almost all of these will work based on ssh-keys or ssh-certs.

I use something like this to open terminals on multiple computers with 1 script:```

#!/bin/bash 
XTERM_OPTS="-u8 -fs 18 -fa Monospace -sb -fg green -bg black"
uxterm -geometry 80x25+0+0 $XTERM_OPTS -e ssh -X comp1 &
uxterm -geometry 80x25+760+355 $XTERM_OPTS -e ssh -X comp2 &
uxterm -geometry 80x25+760+0 $XTERM_OPTS -e ssh -X comp3 &
uxterm -geometry 80x25+760+0 $XTERM_OPTS -e ssh -X comp4 &
```

For non-standard ssh connection settings, my ~/.ssh/config file handles different userids, different ssh-keys, and different ports for each other computer.

---

### Post by coredumped2 on 2018-09-27
I asked the question like I did because I was asked to write a script  for a project with certain requirements. I realize there are many  security issues with what I am asking, as was brought up by others  working on the project, but I have little control over the script  requirements.

I apologize if I offended SeijiSensei, as this was  not my intent. I understand that the password method is not preferred,  but it is what I am being asked to do for the project.

Though I  am new to Linux, I can understand that root access presents a security  risk. The project software being used requires root access on all  computers it is using, therefore we must have root access in order to  use the software. Since the computer network is not attached to the  Internet, perhaps they feel it is an acceptable risk.

If I have violated a forum rule by posting about root use, then I apologize.

I  appreciate you taking time to respond to my question. I will look over  the solutions you listed and see I can use one of them to fulfill what I  need to do.

---

