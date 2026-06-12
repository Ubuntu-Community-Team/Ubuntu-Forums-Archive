---
title: "Samba problems"
date: 2012-03-05
forum: Server Platforms
---

### Post by miffokarnevalen on 2012-03-05
Hi!

First I have to inform you that I'm quite new to linux, even if I have some basic knowlegde and is pretty comfortable with the command line.

As far as my problem then...

I've been through a trouble shooting guide for samba, that I found, but I'm not sure how to interpret the results I'm getting.
As far as I can see the smbd and nmbd services are up and running. I cannot, however, connect to the server from any clients.
From the information/knowledge I have my guess is that it has something to do either with name lookups or possibly with firewall rules.

If I try to list the shares locally on the server with 'smbclient -L localhost -U%' I get a list of the available shares that looks like this:
--------------------------------------------------------------------------
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.11]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (Samba 3.5.11)
    test            Disk      For testing only, please
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.11]

    Server               Comment
    ---------            -------
    RUMPNISSE            
    RUMPNISSEOLD         

    Workgroup            Master
    ---------            -------
    WORKGROUP            RUMPNISSEOLD

----------------------------------------------------------------------

Where "rumpnisse" is the ubuntu server and "rumpnisseold" is my old (soon to retire I hope) W2k server.

If I instead exchange 'localhost' for 'rumpnisse' or the IP adress of the server I get an error message 
"Connection to rumpnisse failed (Error NT_STATUS_UNSUCCESSFUL)"

If I browse the network from my Windows 7 client I can see my linux server listed but if I click on it I get an error saying "The network path cannot be fond" and when I click "further information" W7 tells me that the server is not setup to accept connections on the File&Printer sharing protocol.

My smb.conf is a very basic one to trouble shoot:

-------------------------------------------
[global]
    workgroup = workgroup
[test] 
    comment = For testing only, please
    path = /home/samba
    read only = no
    guest ok = yes
-------------------------------------------

---

### Post by pinjan on 2012-03-05
Can you list what you have in /etc/samba/smb.conf  ?

---

### Post by Morbius1 on 2012-03-05
I think he did:
> My smb.conf is a very basic one to trouble shoot:

-------------------------------------------
[global]
    workgroup = workgroup
[test] 
    comment = For testing only, please
    path = /home/samba
    read only = no
    guest ok = yesWhy people mess with the default smb.conf is beyond me.

We can spend the next 2 hours putting that back to the default or he can start over with the one he hopefully saved before ending up with this one.

As an example of what his smb.conf does:

There is a line missing: "map to guest = Bad User". 
Without that line samba defaults to: "map to guest = Never". 

So an unauthenticated user or a user that does not have a corresponding samba password will never be allowed to be mapped to the guest user account - yet he created a share that allows guest access.

He did post in the "Server" section though so maybe he has some other mechanism in the network to handle network users and passwords.

---

### Post by pinjan on 2012-03-05
> **Morbius1 said:**
> I think he did:
:oops:  it was so much shorter than mine so I didn't notice that

> **Morbius1 said:**
> 
Why people mess with the default smb.conf is beyond me.

We can spend the next 2 hours putting that back to the default or he can start over with the one he hopefully saved before ending up with this one.


Agree, mine is based on default and it works

---

### Post by miffokarnevalen on 2012-03-05
> **Morbius1 said:**
> I think he did:
Why people mess with the default smb.conf is beyond me.

We can spend the next 2 hours putting that back to the default or he can start over with the one he hopefully saved before ending up with this one.

As an example of what his smb.conf does:

There is a line missing: "map to guest = Bad User". 
Without that line samba defaults to: "map to guest = Never". 

So an unauthenticated user or a user that does not have a corresponding samba password will never be allowed to be mapped to the guest user account - yet he created a share that allows guest access.

He did post in the "Server" section though so maybe he has some other mechanism in the network to handle network users and passwords.

I'm not sure what you are saying here.
I think that you mean that with my config a guest will never be allowed to access the share? Nor will an unautheticated user be able to log in as a guest? Is that correct?
If I have  user with a password in the smbpasswd file and try to login with that username and password I should be able to access the share anyway?

The reason why I have "messed" with the default config is that it didn't work with the default. It might be that the problem lies somewhere else though. My intention is not to use the config that I have now. I exchanged it for this "simple" config according to the directions in the trouble shooting guide on samba.org.

---

### Post by Morbius1 on 2012-03-05
the "map to guest = Bad User" was just one example but....

* You have definitely removed all anonymous access to that share from a Linux client unless the client forces itself to pass credentials and then only if there is a corresponding user name and password on the server.

* Windows clients are different in that for reasons never fully explained the Windows client always passes the user's local login user name and password - without being asked.

If you have a corresponding server user name set up and a smbpasswd for that user then the Windows client will be allowed access after providing those credentials. If the smbpasswd matches exactly the Windows local login password then the whole process appears to be transparent since the user is never asked for credentials - he's already passed them.

However, If your intent was to create a share allowing anonymous access then if a Windows client does not have a corresponding user and smbpasswd on the server he will not gain access.

There's an awful lot of user names and passwords flying across the lan for a guest share.

BTW, There's a copy of the factory fresh smb.conf at /usr/share/samba/smb.conf should you need it. It does have one curious mistake though. It sets encrypt passwords to No instead of Yes.

---

### Post by miffokarnevalen on 2012-03-05
If we, for a second, look aside the "so-so" config:

Shouldn't I get the same result with these three lines:

smbclient -L localhost -U%

and

smbclient -L rumpnisse -U%

and

smbclient -L 192.168.21.3 -U% (this is the IP adress of the ubuntu machine)

Only with the first line I get a list of which shares are there and with the other two I get "NT_STATUS_CONNECTION_REFUSED". I cannot really uderstand the difference.

And:
Shouldn't I at least get a _list_ of the shares when browsing the network from a windows machine, even if the user/pass is not correct. The user/pass, I assume, gets sent only when I try to access a share?

For the record:
I have both added the "map to guest = bad user"-line and reverted to the "template"/"stock" config again with no success. The problem remains.

---

### Post by Morbius1 on 2012-03-05
This is the end of the day for me so the more I post the more incoherent I will become - more than before :D

I don't know the answer to the smbclient question off the top of my head. Doing that on my system yield the same results.

> Shouldn't I at least get a _list_ of the shares when browsing the  network from a windows machine, even if the user/pass is not correct.  The user/pass, I assume, gets sent only when I try to access a share?No, because the credentials are past to the server at the workgroup level not the share level. Windows passes these things without being asked. It would be the same thing if from a linux client you passed: smb://user: password@server/share. The server is forced to deal with the credentials from first contact.

After you reset smb.conf you did restart samba right?
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by miffokarnevalen on 2012-03-06
Yes, of course I restarted samba. Even though that should not be necessary as samba scans the config file for changes and applies them accordingly every 60 seconds. At least that's what I read.  However, for some strange reason that I don't have the slightest clue about, things are now functioning. Let's just hope it continues that way. Now I only have to figure out why my printer don't want to be friends with cups, then I can retire my old server.  I want to thank you for making an effort to help me, it's appritiated, even though we did not come to a conclusion of what the problem really was.

---

