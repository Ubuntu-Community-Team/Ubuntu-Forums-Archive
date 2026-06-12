---
title: "Domain Workstation cannot SSH to other Domain joined workstation"
date: 2011-01-11
forum: Server Platforms
---

### Post by Paradox_Wanderer on 2011-01-11
I have a truly freakish thing happening here.  First I'll start with a general map:

Workstation A (10.10.0.100) - Ubuntu 10.10 joined to mydomain.local via likewise-open
Workstation B (10.10.0.101) - Ubuntu 10.10 joined to mydomain.local via likewise-open
Workstation C (10.10.0.102) - Ubuntu 10.10 NOT joined to any domain
Server A (10.10.0.1) - Windows 2003 AD Server on mydomain.local
Server B (10.20.0.1) - Ubuntu 10.10 joined to otherdomain.remote

Okay! So, as you can see I've successfully installed likewise and I've been able to get SUCCESS notifications from the join.  I've been able to log in locally with a domain user and use a domain user password.  I've also added a special Group in AD for linuxadmins and then added that to my /etc/sudoers file so I can sudo from a Domain Account.  Great right?  I'm slowly replacing Windows.  Mwa ha ha ha... Okay but there's a hitch:

I CAN'T SSH FROM MACHINE TO MACHINE!  but it's still not quite that simple.

I can SSH from Workstation A to Workstation C as a Domain User.
I can SSH(Putty) from Server A to Workstation A and B as a Domain User.
I can SSH from Server B to Workstation C as an alternate Domain User.
I can't SSH from Workstation A to Workstation B as a Domain User.
I can SSH from Workstation A to Workstation B as a Local User. 
I can SSH from Workstation B to Workstation A as a Local User.
I can't SSH from Workstation B to Workstation A as a Domain User.

Complicated enough for you?
The simple version is that if it's joined to the domain I can't ssh into another machine that's also joined to the domain while I'm a domain user.
But give me a local account and it's as if there's not problem.

I tried looking through the logs to find something but wasn't about to find a "sshd" type log.  Syslog was completely unhelpful as it doesn't really show anything for the time stamps of my connections.  Where does one start troubleshooting this?

I thought it might be a groups thing like the sudoers file, but I don't have an ssh or sshd group.

Oh and what does SSH do?  What's the error it throws?
```
MYDOMAIN\domainadmin@workstationa:/$ ssh mydomain\\domainadmin@workstationB
The authenticity of host 'WorkstationB (10.10.0.101)' can't be established.
RSA key fingerprint is OB:SC:UR:ED:FR:OM:YO:UF:OR:PR:IV:AC:YR:EA:LL:Y!.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'WorkstationB,10.10.0.101' (RSA) to the list of known hosts.
```
Here it waits for exactly 120 seconds and then...
```
Connection closed by 10.10.0.101
```

What can I do?

---

### Post by Paradox_Wanderer on 2011-01-12
There was one new development:

From Workstation C, I used byobu to ssh into Workstation B (as a domain user) and then opened another window and ssh’d into Workstation A (as a domain user).  Then! I was able to ssh into Workstation B from Workstation A (as a domain user).  But it only worked for a little while.  Probably the length of the Kerberos ticket’s expiration. 

I was able to log in with different users on all the stations so it’s not a user ticket, but I think there might be something wrong with the computer ticket.  Are they the same or separate?

---

### Post by Paradox_Wanderer on 2011-01-12
I posted this in the likewise forums as well.  Someone clued me in to a way to find out what was happening.

For the sake of the googlers, here's what I finally found to solve the problem:

That was EXACTLY the kind of insight I was looking for.  auth.log was worthless.  Didn&#8217;t even show the attempts to log in.  But my friend, I owe you a burger for pointing toward &#8220;ssh -vvv&#8221;.  You know, when you&#8217;ve working on a problem for so long you forget to stop and start making things verbose?

As it turns out SSH was stuck at:
```
Cannot resolve network address for KDC in realm "MYDOMAIN.LOCAL"
```

I though there was an issue with a missing DNS entry.  Maybe some funky programming wants kdc.mydomain.local.  So I added an entry into my DNS server and got a whole lotta nothing.  So I started snooping around and found information about Kerberos Reamls. 

and Bob&#8217;s your Uncle:
```
sudo nano /etc/krb5.conf
```

Jump over to the realms section
```

...
[realms]
...
        MYDOMAIN.LOCAL = {
                auth_to_local = RULE:[1:$0\$1](^MYDOMAIN\.LOCAL\\.*)s/^MYDOMAIN\.LOCAL/MYDOMAIN/
                auth_to_local = RULE:[1:$0\$1](^MYDOMAIN\.LOCAL\\.*)s/^MYDOMAIN\.LOCAL/MYDOMAIN/
                auth_to_local = DEFAULT
        }
```

and put some extras into it ->
```

    kdc = servera.mydomain.local
    kdc = serverc.mydomain.local  #This is a BDC that sits under my desk... just in case...

```
So now the section looks like this:
```

...
|realms|
...
  MYDOMAIN.LOCAL = {
    kdc = servera.mydomain.local
    kdc = serverc.mydomain.local
    auth_to_local = RULE:[1:$0\$1](^MYDOMAIN\.LOCAL\\.*)s/^MYDOMAIN\.LOCAL/MYDOMAIN/
    auth_to_local = RULE:[1:$0\$1](^MYDOMAIN\.LOCAL\\.*)s/^MYDOMAIN\.LOCAL/MYDOMAIN/
    auth_to_local = DEFAULT
}
```

So now not only does everything work, but it&#8217;s super zippy.  It almost feels faster than a local login.

Thanks! This one&#8217;s solved. 

sudo /etc/init.d/OverThrowOfM$ start
./evillaugh

---

### Post by Paradox_Wanderer on 2011-01-12
[http://www.likewise.com/community/index.php/forums/viewthread/949/]("http://www.likewise.com/community/index.php/forums/viewthread/949/")

If anyone wants to read the likewise thread.

---

