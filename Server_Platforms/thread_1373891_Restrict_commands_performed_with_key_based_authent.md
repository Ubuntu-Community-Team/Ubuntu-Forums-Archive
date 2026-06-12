---
title: "Restrict commands performed with key based authentication"
date: 2010-01-06
forum: Server Platforms
---

### Post by dragos2 on 2010-01-06
[FONT=Verdana][SIZE=2]As I stated here [http://ubuntuforums.org/showpost.php?p=8618397&postcount=8](http://ubuntuforums.org/showpost.php?p=8618397&postcount=8)
I read that I can restrict command executed on a remote server using key based
authentication like this([http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html):]("http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html%29:")[/SIZE][/FONT][FONT=Verdana][SIZE=2]

```

from="someserver.subdomain.com",no-X11-forwarding,noagent-forwarding ssh-rsa
command="rsync -vvztPre "ssh -p 22" /localfile user@server:/remote/path
" AAAAC4MybC1yc2EAAAABIwAAAQEAybmcqaU/Xos/GhYCzkV+kDsK8+A5OjaK5WgLMqm
u38aPo56Od10RQ3EiB42DjRVY8trXS1NH4jbURQPERr2LHCCYq6tHJYfJNhUX/COwHs
+ozNPE83CYDhK4AhabahnltFE5ZbefwXW4FoKOO+n8AdDfSXOazpPas8jXi5bENf7he
ZT++a/Qxbu9JHF1huThuDuxOtIWl07G+tKqzggFVknM5CoJCFxaik91lNGgu2OTKfY9
4c/ieETOXE5L+fVrbtOh7DTFMjIYAWNxy4tlMR/59UVw5dapAxH9J2lZglkj0w0LwFI
+7hZu9XvNfMKMKg+ERAz9XHYH3608RL1RQ== This comment describes key #2

```[/SIZE][/FONT] [FONT=Verdana][SIZE=2]

The problem is that I want to be able to execute 2 different commands, one being
```

[/SIZE][/FONT][FONT=Verdana][SIZE=2]rsync -vvztPre "ssh -p 22" /localfile user@server:/remote/path

```[/SIZE][/FONT][FONT=Verdana][SIZE=2]

and the other

```

rf /some/path/*

```Any ideas of how to achieve this ?
 

[/SIZE][/FONT]

---

### Post by Muttley99 on 2010-01-06
try;

ssh -tvvv someone@IP -p 22 'sudo rsync xxx ......'

if you get a permission error, check that you have your user added to the sudoers file to require NOPASSWD for rsync.

BTW. have you just shared your public key with the world?

---

### Post by dragos2 on 2010-01-07
> **Muttley99 said:**
> try;

ssh -tvvv someone@IP -p 22 'sudo rsync xxx ......'

if you get a permission error, check that you have your user added to the sudoers file to require NOPASSWD for rsync.

BTW. have you just shared your public key with the world?

I don't understand ? I can execute remote ssh commands like this:
ssh user@host 'command'

But I wanted a way If I log in with that key to be able only to execute 2 commands.
I don't want to be able to do everything when logging in via key.

Lol no, it was an example.

---

### Post by BkkBonanza on 2010-01-07
I've been thinking about your problem. So far the only way I've thought of is to put a script on the server and limit your key to that script. Then pass an environment variable when you call the script to determine whether the script will call rsync or call rf, as you need.

You can pass the environment by calling ssh a bit differently, 
eg.

CMD=BACKUP ssh user@host cmdscript

This sets the env before ssh runs. The key will limit you to the script as command but the script is only capable of doing two things and you choose which with the env variable CMD.

Another way I thought of is to use two keys and call ssh with -i to choose. But this doesn't extend as well if you need more commands later.

---

### Post by dragos2 on 2010-01-07
> **BkkBonaza said:**
> I've been thinking about your problem. So far the only way I've thought of is to put a script on the server and limit your key to that script. Then pass an environment variable when you call the script to determine whether the script will call rsync or call rf, as you need.

You can pass the environment by calling ssh a bit differently, 
eg.

CMD=BACKUP ssh user@host cmdscript

This sets the env before ssh runs. The key will limit you to the script as command but the script is only capable of doing two things and you choose which with the env variable CMD.

Another way I thought of is to use two keys and call ssh with -i to choose. But this doesn't extend as well if you need more commands later.

Hmm, thank you for this but it is too complex and can be hard to maintain.

I like WinScp since it has this autoresume but I have to copy the backup to a Windows
station and upload from there..

I am open to suggestions :)

---

### Post by slakkie on 2010-01-07
I have something for you, but I need to look it up (and rewrite it a bit):

Add the following in your your authorized keys from, before the rsa-ssh part:

```

   from="IP.add.re.ss",command="/home/user/bin/validate-commands"

```

```

# Create the homedir and edit the validate-commands file
$ mkdir /home/user/bin
$ vi /home/user/bin/validate-commands

```

```

#!/bin/sh
# File: validate-commands

# echo $SSH_ORIGINAL_COMMAND > /tmp/sshorig

case "$SSH_ORIGINAL_COMMAND" in
        *\&*)
                echo "Rejected"
                ;;
        *\(*)
                echo "Rejected"
                ;;
        *\{*)
                echo "Rejected"
                ;;
        *\;*)
                echo "Rejected"
                ;;
        *\<*)
                echo "Rejected"
                ;;
        *\`*)
                echo "Rejected"
                ;;
        telnet)
                $SSH_ORIGINAL_COMMAND
                ;;
        *)
                echo "Rejected"
                ;;
esac

```

Now make it executable.

```

$ chmod +x /home/user/bin/validate-command

```

See also: [http://www.jdmz.net/ssh/](http://www.jdmz.net/ssh/)

---

### Post by BkkBonanza on 2010-01-07
I like that $SSH_ORIGINAL_COMMAND variable. I think I would simplify the validation. Just compare exactly for the two allowed commands and reject any other.
But this is quite workable and easy to setup and use.

---

