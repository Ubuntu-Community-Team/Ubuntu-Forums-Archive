---
title: "ssh log terminal input from server to a txt file"
date: 2012-06-18
forum: Server Platforms
---

### Post by StGeorge on 2012-06-18
I am using Ubuntu 10.04, (desktop computer), to connect via Terminal with SSH to a Web Hosting Server.

The Web Hosting Server is cPanel. Permission has been given to access via SSH.

The reason is to monitor CPU usage.

I have connected OK using:
```
ssh username@theDomain -p 1234
```
followed by my password

I then type 'top' to access the data showing amongst other things the user and process CPU

What I wish to do is this:

1/ Automatically log the input data to a txt file as the running processes go too fast screen wise to take the data.
(Is this already done automatically, if so where is the file?)

2/ Login automatically by creating SSH keys with a Terminal Command.
(I have tried following the guides but nothing seems to work).
Do I have to generate the keys in cPanel First?

Any help on the above issues would be appreciated.

Thanks in advance.

---

### Post by sanderj on 2012-06-18
You can use tcl-expect send-expect sequence to mimic your interactive (SSH) session. You can write such a script by hand, or ... use autoexpect to generate the raw script automagically (and then only clean it up manually).

autoexpect is some (gzipped) file in some subdirectory. I'll have to find where / how to install ...

---

### Post by sanderj on 2012-06-18
Found it:

```
sudo apt-get install expect-dev
```

Usage:

autoexpect ssh  [email]sander@example.com[/email]
autoexpect started, file is script.exp

<do your thing>
<type exit>

autoexpect done, file is script.exp
sander@R540:~$ 

You can then clean up script.exp, and then run it from tcl/expect.

---

### Post by StGeorge on 2012-06-18
I think I have just blacklisted myself from the server.

Is this file saved on the Server then?

I was hoping to save it locally.

I typed:
```
sudo gedit script.exp
```

was asked for my password
entered my computer password
tried three times
now I think I am locked out.

It looks like it is saved in the server.
> xxxxxxxx is not in the sudoers file.  This incident will be reported.

Well at least I am not locked out of the Server I have just logged in again.

So will just wait for a rollicking for not knowing what I am doing, lol.

---

### Post by sanderj on 2012-06-18
No, it's saved locally on your 'client' computer.

And: do not use 'sudo' to edit a normal file.

---

### Post by StGeorge on 2012-06-18
@sanderj
Thanks.
It has installed OK
I have logged in with the command.
Will leave the process list running for a while.

I did not realize I was still logged into the Server when I tried to open the file.
I used:
```
q
then 
exit
```

I should have opened a new Terminal Tab, (local machine), and typed:
```
gedit script.exp
```

---

### Post by sanderj on 2012-06-18
> **StGeorge said:**
> 
Will leave the process list running for a while.



Better to not do that: that will result in an enormous script.exp, which will be almost impossible to edit.

Correct way: hit & run.

So:
autoexpect ssh blabla
<login>
do one thing
exit


then edit script.exp, meaning: use it as a basis for your own script.

---

### Post by StGeorge on 2012-06-18
@sanderj
Thanks:
See what you mean by leaving it too long.

---

