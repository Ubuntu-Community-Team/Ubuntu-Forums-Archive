---
title: "How to securely store sensitive variables so they can be accessed by your scripts"
date: 2017-02-16
forum: Security
---

### Post by horsebox2 on 2017-02-16
I'm setting up various configuration tools and stuff for automatically setting up Ubuntu distros and docker containers and stuff like that. Some of the scripts need sensitive data. Heres an example:

```
#!/usr/bin/expect -f

set force_conservative 0  ;# set to 1 to force conservative mode even if
              ;# script wasn't run conservatively originally
if {$force_conservative} {
    set send_slow {1 .1}
    proc send {ignore arg} {
        sleep .1
        exp_send -s -- $arg
    }
}

set timeout -1
spawn heroku login
match_max 100000
expect -exact "Enter your Heroku credentials.\r
Email: "
send -- "MY_SENSITIVE_USERNAME\r"
expect -exact "MY_SENSITIVE_USERNAME\r
Password (typing will be hidden): "
send -- "MY_SENSITIVE_PASSWORD\r"
expect eof
```

its an expect script which logs into heroku (the same script could be used to log into any website). So it needs the username and password. This is just one example, there are loads of these bits of sensitive data needed by various scripts. Is there a secure way to store them so they can be securely accessed by your scripts? The thing is I need to upload it all including the usernames and passwords to git so that the rest of the theme can use it, and also to the docker hub. So there are two things I need to figure out, first is how to securely put these credentials under version control (we'll use a private git repo so maybe thats enough. And two, how to securely store and access them after the scripts are installed and run on the machine. 

So for issue one, would it be best to encrypt a config file? The confiig files will need to change a bit each time a new system is setup so the user needs to be able to edit them. 

For issue two, I assume storing them as environment variables is extremely insecure. The scripts will be run with super user privileges though, so maybe there are environment variables that are only available to superuser? Or would it be better to store them in config files that can only be read by superusers? Or is there an even better approach to this? Would public and private keys be of any use here? Each machine is going to have the same public and private key but these keys are gonna be stored on github too and also any hacker without superuser privileges could just get them from the home directory. 

There are probably a million ways of doing this, such as gsettings (preferably we wanna make things platform independent though), sqlite database, but the simpler and easier the better, no point going a thousand more miles to gain only a single mile in added security.

---

### Post by TheFu on 2017-02-16
You cannot put credentials in github and expect them to remain secret.  

Keep those separate and rethink how you handle them. It would be smart to place them into a file in /root/.hidden-creds-for-x-project and make it 600. That is the best practice. /root is locked down. Then tell the user to make those changes in the INSTALL file and have your setup scripts verify the required localization happened.

Never put credentials into git (even a private repo).  
Never put private keys in a place that anyone else can access. Never reuse private keys on more than 1 machine. There are so many reasons for this - google it.

Reusing the same private key is foolish. Don't.  Please.  Don't.  Google all the times someone did this and their connection/security was hacked. There are some pretty big people burned by doing this. Don't.

Lastly, I wouldn't use expect anymore. It was a tool created for rsh and telnet days.  These days people tend to use devops tools like Ansible. There are thousands of pre-existing tasks, rolls, playbooks already available on the web. Ansible has minimal dependencies compared to all the other options - basically python, 2 python libraries and ssh.  In 14.04, all the python stuff was pre-installed. In 16.04, I've had to load them manually before ansible would work.

Anyway, hopefully this helps.

---

