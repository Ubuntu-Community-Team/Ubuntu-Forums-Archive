---
title: "using ubuntu instead of freenas"
date: 2007-10-18
forum: Server Platforms
---

### Post by meharts on 2007-10-18
Hi to everyone at ubuntu forum. I am new in town and could do with a few pointers if anyone has the time.
I have had friends go on about using ubuntu as a nas server instead of freenas, openfiler, and naslite. 
Using the above servers I have been used to installing my distro and going to another computer and logging in to my server to do the necessary changes, updates etc. 
They all have similar attributes - a friendly user interface.
I installed Gutsy today but can't find how to get access to the server.
I set up my network card while installing but wasn't asked for dns server  settings? My server is behind a firewall with stationary ip addresses, so as you all well know I can't get access to the Internet until I set up my network fully.
I have to admit that I am not to knowledgeable when it comes to working from the command console - but I am learning.
Is the whole idea behind ubuntu's server that you work from the command line?
Can anyone give me a little help in getting started?
Would appreciate any help I can get on this matter.
Thanks!

meharts

---

### Post by meharts on 2007-10-19
Well, since posting this mail I have been up nearly all night browsing your forum for answers to my questions.

I installed all packages that were permitted during the installation. I had no errors what so ever.

After the install, I have tried to become root, install, ubuntu desktop, without success!! I receive error codes for everything I do!!

I can't get access to the web because I am behind my fire-wall- An example of my settings would be:
  Stationary Ip address.     192.168.0.xxx
   net mask                           255.255.255.0
   Standard gateway          192.168.0.1
   DNS server 1                   195.54.122.200
   DNS server 2                   195.54.122.204 

My problem is, as I have explained, I don't know how to add my dns server settings from the command line. A lot of distros have that built in when you install from the beginning. Why doesn't ubuntu have that?!!

I don't mind working to make my server work but this is ridiculous. I have searched and searched for some information that I can understand - but as yet been unsuccessful. 

I am no genius when it comes to Linux but have been installing the different distros that are available and manage to get things working, but ubuntu I haven't a clue?!!

I could go the easy way and connect directly to the net and change my settings later. Just don't see why I need to disconnect/reconnect my home network just to get the server working.

Please! please! can someone put me on the right track.

I have been able to access apache from another computer. When I opened the folder it said " It Works" or something like that!!

What works? Certainly not ubuntu at the moment!!

meharts

---

### Post by meharts on 2007-10-19
Well, I can give you the error information that comes up with every attempt I do.

sudo passwd root
sendmail:fatal:open /etc/postfix/main.cf: no such file or directory

I hope that info gives someone some ideas.

meharts

---

### Post by tkharris on 2007-10-19
Open root terminal:

nano -w /etc/resolv.conf

Add:

nameserver 195.54.122.200
nameserver 195.54.122.200

DNS issue should now be fixed.

If you're going to be running a server you should have basic knowledge of the following files:

/etc/resolv.conf
/etc/hosts
/etc/hosts.deny
/etc/hosts.allow

And the following programs:

ifconfig
netstat
( lots more, but start with those two )

---

### Post by meharts on 2007-10-19
Hi tkharris, I appreciate you taking the time to help me with my problem. I am learning the command structure - but it is easy to be come accustomed to doing things the easy way.

Thanks again
meharts

---

