---
title: "Expect for Rsync"
date: 2008-12-13
forum: Server Platforms
---

### Post by etechship on 2008-12-13
I know that there are a lot of other turorials out there, but none of them seem to be working for me, as I have a special ssh command I need to run to make my rsync work. This is my shell script:
```

#!/usr/bin/expect -f

##upload files
spawn rsync -avhze \'ssh -p 2222\' /root/upload ucstream@74.53.96.66:/home/ucstream/vids/new
expect "*ucstream@74.53.96.66's password:*"
send "*password*\n"
expect eof

```


And it's outputting:
> 
spawn rsync -avhze 'ssh -p 2222' /root/upload ucstream@74.53.96.66:/home/ucstream/vids/new
Missing trailing-' in remote-shell command.
rsync error: syntax or usage error (code 1) at main.c(348) [sender=2.6.9]
send: spawn id exp6 not open
    while executing
"send "*password*\n""
    (file "./test.sh" line 6)


Thanks for any help

dave

---

### Post by MJN on 2008-12-13
Have you tried limiting expect to only match the bear minimum?

e.g.

```
expect "password:"
```Is there anything unusual about your password?

Mathew

---

### Post by MJN on 2008-12-13
**<urgent pm sent to etechship!>**

---

### Post by etechship on 2008-12-13
I had the same output when I changed that line.

dave

---

### Post by etechship on 2008-12-13
I have to login to port 2222 for ssh, not the regular port 22, that is what is different for this that I don't see at other tutorials. I think the ' is messing it up some how ...

---

### Post by MJN on 2008-12-13
Does the rsync command, as written, work from the command line without problems?

Mathew

---

### Post by etechship on 2008-12-13
nope, because it needs to be run in /usr/bin/expect -f

dave

---

### Post by etechship on 2008-12-13
oh, I read that wrong.

This is the command I use to upload my files before working with expect:

```
rsync -avhze 'ssh -p 2222' /root/upload/* ucstream@74.53.96.66:/home/ucstream/vids/new/
```

---

### Post by etechship on 2008-12-13
I was just playing with it while I was waiting to here from you, and I got this working. Here is my final script. (and btw, just for searches, I am uploading to a Hostgator web account, so that is why the werid 2222 port for ssh).


```
#!/usr/bin/expect -f

##upload files
spawn rsync -avhze "ssh -p 2222" /root/upload/ ucstream@74.53.96.66:/home/ucstream/vids/new/
expect "password:"
send "*password*\n"
expect eof

```

---

### Post by MJN on 2008-12-13
[Edit: We posted at the same time - good to see you got it working!]

I think you're right about the ' - I didn't spot the  *Missing trailing-' in remote-shell command *error.

I'm not familiar with expect, or spawn particular, and so I guess the problem may well be subtle nuances with how quotes are handled. You'd think escaping them with \ would work though...

Mathew

---

### Post by MJN on 2008-12-13
Password!

---

### Post by etechship on 2008-12-13
boy, I gotta work on copying my code

I'll change it, but I already got a different one on my server

dave

---

### Post by MJN on 2008-12-13
:lolflag:

---

