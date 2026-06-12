---
title: "Linux better but harder to manage ?"
date: 2009-05-30
forum: The Cafe
---

### Post by Mosaab on 2009-05-30
with time I find great things in linux that makes me unable to change back to windows OS, but there are things that I cant find an answer for.

if you look at linux you will find it a great OS specially as a server.. but why things are not getting easy?

lets say for example, in windows you create a domain with a wizard, and clients can join a domain by simply type the domain name you wish to join and the admin username and pass.

why linux community or any ditro maker did not until now create such a thing.?
when creating a linux domain I have to have a huge "to do list" to follow .. and its nearly impossible to memorize all the things to do to achieve such a goal.

---

### Post by albinootje on 2009-05-30
> **Mosaab said:**
>  lets say for example, in windows you create a domain with a wizard, and clients can join a domain by simply type the domain name you wish to join and the admin username and pass.

You're asking a Linux distribution to be compatible with some other setup and/or protocol from some other proprietary OS. 
Well, in a "perfect world" that would be easy when the other OS would want to be compatible too.

.. You do realise that sometimes open source developers have to reverse engineer ?

Here's a relevant example : [http://en.wikipedia.org/wiki/Reverse_engineering#Binary_software](http://en.wikipedia.org/wiki/Reverse_engineering#Binary_software)
> 
The Samba software, which allows systems that are not running Microsoft Windows systems to share files with systems that are, is a classic example of software reverse engineering[9], since the Samba project had to reverse-engineer unpublished information about how Windows file sharing worked, so that non-Windows computers could emulate it.


And there is actually various projects which try to make this, and/or other things easier, there's e.g. 

eBox : [http://en.wikipedia.org/wiki/EBox](http://en.wikipedia.org/wiki/EBox)
OpenFiler : [http://en.wikipedia.org/wiki/Openfiler](http://en.wikipedia.org/wiki/Openfiler)
FreeNAS : [http://en.wikipedia.org/wiki/FreeNAS](http://en.wikipedia.org/wiki/FreeNAS)

And if you look at the various releases of Ubuntu you can see that there has been changes to make the LDAP client installation+configuration easier.

eBox is in the Ubuntu repositories by the way.

And as a disclaimer : 
I found OpenFiler interesting (A friend of mine uses it at work), but not easy to set up, afair I think the project likes you to buy the admin manual.
I have tried eBox for a while, and.. it was not for me, although I like the idea.
And I tried FreeNAS, but after reading various reviews about it, and seeing that some things are not implemented, and that the main developer behind it, is busy, I decided to continue with "LDAP+Samba from scratch".

---

### Post by albinootje on 2009-05-30
See also here, about the future of Samba : [http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

---

### Post by Mosaab on 2009-05-30
you are right .. 
but does such a thing exist even for native linux systems ?

---

### Post by chucky chuckaluck on 2009-05-30
> **Mosaab said:**
> if you look at linux you will find it a great OS specially as a server.. but why things are not getting easy?

the one thing i have learned from using arch is that 'easy' and 'simple' are two way different things. 'easy' requires automation, which means you losing sight of the process. 'simple' is like driving a stick instead of an automatic, or hitting a blade instead of a cavity-back.

---

### Post by albinootje on 2009-05-30
> **Mosaab said:**
> you are right .. 
but does such a thing exist even for native linux systems ?

You can easily set up NIS + NFS for centralized Linux logins + shared /home .. it is insecure, plain-text passwords over the network, and the NFS shares are not protected againt malicious intruders inside the network, but.. it's easy.

The more complex, but more secure way is LDAP.

I suggest you try eBox (See also the "disclaimer" I've just added in my previous comment), it makes LDAP+Samba+Jabber and more very easy to set up, but.. I recommend to try it on a stand-alone machine (not in a VPS or as packages).

---

### Post by Mosaab on 2009-05-30
I took alook at ebox .. man its amazing .. its something like webmin isnt it ?

and actually I am with chucky chuckaluck about easy things makes you loose sight of the process .. but sometimes you have to choose or at least you wanna make things fast when you have huge work to do.

I tried to install ebox .. but because I am running linux mint the terminal says that I have to have some dependencies and I dont know where to get them ... or lets say I am not really an experienced user in linux yet .. and thats why exactly I started this thread. lol

---

### Post by Mosaab on 2009-05-30
I tried to install ebox but i get this:
mosab@mosab-lap ~/Desktop $ sudo apt-get install "^ebox-.*"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ebox-openvpn for regex '^ebox-.*'
Note, selecting ebox-ca for regex '^ebox-.*'
Note, selecting ebox-network for regex '^ebox-.*'
Note, selecting ebox-dhcp for regex '^ebox-.*'
Note, selecting ebox-mailfilter for regex '^ebox-.*'
Note, selecting ebox-jabber for regex '^ebox-.*'
Note, selecting ebox-webserver for regex '^ebox-.*'
Note, selecting ebox-egroupware for regex '^ebox-.*'
Note, selecting ebox-mail for regex '^ebox-.*'
Note, selecting ebox-dns for regex '^ebox-.*'
Note, selecting ebox-trafficshaping for regex '^ebox-.*'
Note, selecting ebox-ntp for regex '^ebox-.*'
Note, selecting ebox-software for regex '^ebox-.*'
Note, selecting ebox-usersandgroups for regex '^ebox-.*'
Note, selecting ebox-samba for regex '^ebox-.*'
Note, selecting ebox-objects for regex '^ebox-.*'
Note, selecting ebox-squid for regex '^ebox-.*'
Note, selecting ebox-printers for regex '^ebox-.*'
Note, selecting ebox-services for regex '^ebox-.*'
Note, selecting ebox-firewall for regex '^ebox-.*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ebox-ca: Depends: ebox (>= 1.0) but it is not going to be installed
           Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-dhcp: Depends: ebox (>= 1.0) but it is not going to be installed
             Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-dns: Depends: ebox (>= 1.0) but it is not going to be installed
            Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-egroupware: Depends: ebox (>= 1.0) but it is not going to be installed
                   Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-firewall: Depends: ebox (>= 1.0) but it is not going to be installed
                 Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-jabber: Depends: ebox (>= 1.0) but it is not going to be installed
               Depends: ebox (< 1.0.10) but it is not going to be installed
               Depends: jabberd2-ldap-bdb but it is not installable
  ebox-mail: Depends: ebox (>= 1.0) but it is not going to be installed
             Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-mailfilter: Depends: ebox (>= 1.0) but it is not going to be installed
                   Depends: ebox (< 1.0.10) but it is not going to be installed
                   Depends: unzoo but it is not installable
  ebox-network: Depends: ebox (>= 1.0) but it is not going to be installed
                Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-ntp: Depends: ebox (>= 1.0) but it is not going to be installed
            Depends: ebox (< 1.0.10) but it is not going to be installed
            Depends: ntp-server but it is not installable
  ebox-objects: Depends: ebox (>= 1.0) but it is not going to be installed
                Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-openvpn: Depends: ebox (>= 1.0) but it is not going to be installed
                Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-printers: Depends: ebox (>= 1.0) but it is not going to be installed
                 Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-samba: Depends: ebox (>= 1.0) but it is not going to be installed
              Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-services: Depends: ebox (>= 1.0) but it is not going to be installed
                 Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-software: Depends: ebox (>= 1.0) but it is not going to be installed
                 Depends: ebox (< 1.0.10) but it is not going to be installed
                 Depends: esofttool (>= 0.4.1) but it is not going to be installed
  ebox-squid: Depends: ebox (>= 1.0) but it is not going to be installed
              Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-trafficshaping: Depends: ebox (>= 1.0) but it is not going to be installed
                       Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-usersandgroups: Depends: ebox (>= 1.0) but it is not going to be installed
                       Depends: ebox (< 1.0.10) but it is not going to be installed
  ebox-webserver: Depends: ebox (>= 1.0) but it is not going to be installed
                  Depends: ebox (< 1.0.10) but it is not going to be installed
E: Broken packages

---

### Post by Mosaab on 2009-05-30
you know what ? I seed to CHAT with some one who has knowledge in windows domain VS Linux domains ... cause I guess I have alot of missunderstanding what a domain means .. I cant find exactly the meaning of domain for linux until now .. 

who can help me on this ?

please excuse my ignorance in this but I really feel like knowing this..

---

### Post by stwschool on 2009-05-30
I'd not say linux is harder to manage. I teach, and have to maintain the computer lab and staff computers. The staff computers run linux and the lab runs a dual-boot as some things we teach require windows. The linux bit's a shedload easier and I can get much more done remotely thanks to the power of the command line over SSH. Easy, I made a php script, which links to a mysql database storing all the ips, user and password for all computers. I enter a sequence of commands and the php script executes that command on all the computers at once. Easy? Damn right. That's why linux is a piece of cake to manage. I'm working much less these days!

---

### Post by albinootje on 2009-05-31
> **Mosaab said:**
> I tried to install ebox but i get this:
mosab@mosab-lap ~/Desktop $ sudo apt-get install "^ebox-.*"


Please try eBox on a stand alone machine from the iso from the eBox website.
And 
```

sudo apt-get -f install

```
might resolve the problem or.. give you some more information why the installation didn't work.

---

### Post by albinootje on 2009-05-31
> **Mosaab said:**
> I took alook at ebox .. man its amazing .. 

I suggest to try and test it first.

I found eBox quite annoying to work with in a VPS (because eBox likes to do everything, including networking for you), but I'm sure it can be very nice in a stand-alone setup.
> 
its something like webmin isnt it ?

Yes. Something like that, except that webmin is more generic and not that closely integrated in Ubuntu. 
Webmin provides a deb file for installation, but that might be focused on Debian rather than Ubuntu.

---

### Post by Mosaab on 2009-05-31
> **albinootje said:**
> Please try eBox on a stand alone machine from the iso from the eBox website.

why do I have to do that ? 


> might resolve the problem or.. give you some more information why the installation didn't work.

I posted the error message of apt-get, check my last post

---

### Post by albinootje on 2009-05-31
> **Mosaab said:**
> why do I have to do that ? 

It is up to you what to do, but in that scenario eBox is much more likely to work correctly.
> 
I posted the error message of apt-get, check my last post

You posted the output of 
```

sudo apt-get install "^ebox-.*"

```
and not from :
```

sudo apt-get -f install

```
Those are two completely different things, although I doubt that "apt-get -f install" will show you more error details.
It will probably de-install the conflicting packages for you.

---

### Post by Mosaab on 2009-05-31
> **albinootje said:**
> ```

sudo apt-get -f install

```

gave me the exact message generated by 
```

sudo apt-get install

```

---

### Post by Mosaab on 2009-05-31
by the way .. I am using linux mint 6, which is based on ubuntu 7.10. does that make any difference ?

---

### Post by Chame_Wizard on 2009-05-31
You only need

```
sudo apt-get install ebox
```

---

### Post by chucky chuckaluck on 2009-05-31
> **Mosaab said:**
> and actually I am with chucky chuckaluck about easy things makes you loose sight of the process .. but sometimes you have to choose or at least you wanna make things fast when you have huge work to do.

for most of us, no choice is going to be perfect, so at any given time, you have to go with what's going to work best for you. that may be linux for some, or windows for others, or even a mac. as you use any OS, though, your learning can increase and that changes which choice is going to be best for you.

---

