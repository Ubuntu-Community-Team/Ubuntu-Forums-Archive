---
title: "Automated command line password change"
date: 2008-10-06
forum: Security
---

### Post by Smokin.joe on 2008-10-06
Hello --

I am  trying to setup an automated password change process. 

I want to be able to SSH into the server and change the user’s password.  The problem I currently have is how to pipe the SSH user password back to the system to complete the Admin authentication process.  
Terminal Output

PASS=`mkpasswd newPassword`;sudo -S  usermod -p $PASS username
[sudo] password for nameduser:

End Terminal Output.
I want to be able to pass the password for the logged in user as part of the script. 

Any suggestion on how to do this?

Thank you 

Joe

---

### Post by cdenley on 2008-10-06
ignore this

---

### Post by cdenley on 2008-10-06
Put this script in, for example, /usr/bin/setpass.py
```

#!/usr/bin/env python
import md5,sys,os,string,random

# Based on FreeBSD src/lib/libcrypt/crypt.c 1.2
# http://www.freebsd.org/cgi/cvsweb.cgi/~checkout~/src/lib/libcrypt/crypt.c?rev=1.2&content-type=text/plain

# Original license:
# * "THE BEER-WARE LICENSE" (Revision 42):
# * <phk@login.dknet.dk> wrote this file.  As long as you retain this notice you
# * can do whatever you want with this stuff. If we meet some day, and you think
# * this stuff is worth it, you can buy me a beer in return.   Poul-Henning Kamp

# This port adds no further stipulations.  I forfeit any copyright interest.

def md5crypt(password, salt, magic='$1$'):
    # /* The password first, since that is what is most unknown */ /* Then our magic string */ /* Then the raw salt */
    m = md5.new()
    m.update(password + magic + salt)

    # /* Then just as many characters of the MD5(pw,salt,pw) */
    mixin = md5.md5(password + salt + password).digest()
    for i in range(0, len(password)):
        m.update(mixin[i % 16])

    # /* Then something really weird... */
    # Also really broken, as far as I can tell.  -m
    i = len(password)
    while i:
        if i & 1:
            m.update('\x00')
        else:
            m.update(password[0])
        i >>= 1

    final = m.digest()

    # /* and now, just to make sure things don't run too fast */
    for i in range(1000):
        m2 = md5.md5()
        if i & 1:
            m2.update(password)
        else:
            m2.update(final)

        if i % 3:
            m2.update(salt)

        if i % 7:
            m2.update(password)

        if i & 1:
            m2.update(final)
        else:
            m2.update(password)

        final = m2.digest()

    # This is the bit that uses to64() in the original code.

    itoa64 = './0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'

    rearranged = ''
    for a, b, c in ((0, 6, 12), (1, 7, 13), (2, 8, 14), (3, 9, 15), (4, 10, 5)):
        v = ord(final[a]) << 16 | ord(final[b]) << 8 | ord(final[c])
        for i in range(4):
            rearranged += itoa64[v & 0x3f]; v >>= 6

    v = ord(final[11])
    for i in range(2):
        rearranged += itoa64[v & 0x3f]; v >>= 6

    return magic + salt + '$' + rearranged

def getsalt(length):
    chars = string.letters + string.digits
    ret=""
    for i in range(length):
        ret+=random.choice(chars)
    return ret

if len(sys.argv)<3:
    print "You need to give a username and password"
    print "usage: setpass.py user password"
    sys.exit(2)
user=sys.argv[1]
passplain=sys.argv[2]
passcrypt=md5crypt(passplain, getsalt(8))
os.system("usermod -p "+passcrypt.replace("$","\\$")+" "+user)

```
set the permissions
```

sudo chown root:root /usr/bin/setpass.py
sudo chmod 700 /usr/bin/setpass.py

```
Now, whenever you want to change someone's password, run
```

sudo setpass.py user pass

```
Be aware, however, that the utilities included in linux don't allow you to give plaintext passwords as arguments for a very good reason. This would not be the safest approach to changing passwords.

---

### Post by Smokin.joe on 2008-10-06
I really appreciate your response -- thank you. 

One item to note however -- The mkpasswd command does encrypt the password.  The line I posted encrypts the password and stores it in the variable PASS.  I then call usermod w/ the -p and pass it my encrypted password variable, $PASS.  Apart form being prompted for the password the string I posted works fine.  

I will review the script posted by you.  Again, I want to thank you for your thoughts.

---

### Post by rovae on 2008-10-06
The fashion [shawl](http://www.shawls-store.com) is a lace [Pure Wool Shawls](http://www.shawls-store.com/shawls-pure-wool-shawls-c-4_14.html) knit from the bottom point to the top edge, which is finished with an attached I-cord edge. [Shawls](http://www.shawls-store.com/shawls-c-4.html) are then picked up along the edges and worked off together with the [wrap](http://www.shawls-store.com). This [knitting shawl](http://www.shawls-store.com) is not painfully difficult, but may require thinking and persistence from the less experienced, since I have not charted the whole thing.

---

### Post by cdenley on 2008-10-06
> **Smokin.joe said:**
> I really appreciate your response -- thank you. 

One item to note however -- The mkpasswd command does encrypt the password.  The line I posted encrypts the password and stores it in the variable PASS.  I then call usermod w/ the -p and pass it my encrypted password variable, $PASS.  Apart form being prompted for the password the string I posted works fine.  

I will review the script posted by you.  Again, I want to thank you for your thoughts.

Sorry, I missed that. You might want to use the md5 hash algorithm.
```

mkpasswd -H md5 newpass

```
I didn't even know about the mkpasswd command, so thanks. I guess I reinvented the wheel.

---

### Post by cdenley on 2008-10-07
```

sudo usermod -p `mkpasswd -H md5 newpass` username

```

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

