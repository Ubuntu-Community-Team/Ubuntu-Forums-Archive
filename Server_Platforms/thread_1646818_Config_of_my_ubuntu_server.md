---
title: "Config of my ubuntu server"
date: 2010-12-16
forum: Server Platforms
---

### Post by seizart on 2010-12-16
Hello

I have a domain name which point to my static public ip adress, my ubuntu is behind a dlink router.

I would like to config my ubuntu server so that my server is accessible from outside my local network but ALSO from inside my local network with my domain name.

I manage to access from outside by port forwarding in my router but i can t access my server through my domain name inside my local network, only via the local ip adress (192.168.0.etc..) which i don t want.

I know my question is really specific and it might take somebody who has some network knowledge but i would like to get some help since i looking for a solution for months ....

Hope evrything is clear.

Thanks a lot:D

---

### Post by stlsaint on 2010-12-16
What do you mean when you say "You are unable to access the domain from within the local network?" If you have port forwarding setup and you can access from outside lan than you must be able to access within lan!!
Are you saying that when you are on LAN you are unable to go to:
[www.mydomain.com](www.mydomain.com) and reach your site?
If so than you need to:
1. Ensure that your domain provider is using the correct public ip address.
2. Ensure that you have apache up and running on website.

---

### Post by karlson on 2010-12-16
> **seizart said:**
> Hello

I have a domain name which point to my static public ip adress, my ubuntu is behind a dlink router.

I would like to config my ubuntu server so that my server is accessible from outside my local network but ALSO from inside my local network with my domain name.

I manage to access from outside by port forwarding in my router but i can t access my server through my domain name inside my local network, only via the local ip adress (192.168.0.etc..) which i don t want.

I know my question is really specific and it might take somebody who has some network knowledge but i would like to get some help since i looking for a solution for months ....

Hope evrything is clear.

Thanks a lot:D

If you have DNS server in your network set the A record to your server's IP address.

If you don't then put in FQDN into hosts file.

---

### Post by seizart on 2010-12-16
Thanks a lot for your reply.

To be more explicit and to be sure my problem is well understood:

_I can_ access my website (hosted in a computer inside my localnetwork) from any computer outside my localnetwork through the [www.mydomain.com](www.mydomain.com)
So i think my domain provider is correctly using my ipadress and my port redirection should be fine

**I can't** access my website from any computer inside my localnetwork through the [www.mydomain.com](www.mydomain.com), but i can access with the local ip adress (192.168.0.197)


Obviously what i want is to use the [www.mydomain.com](www.mydomain.com) adresss both locally and outside my network

Could you be more explicit about ''FQDN into hosts file.'' as i don t know exactly how to do that.

Many thanks

---

### Post by arrrghhh on 2010-12-16
In the client hosts file, you place a DNS record pointing 192.168.0.197 to [www.mydomain.com](www.mydomain.com).  Depending on the client you're using, the location of the hosts file will be different.

You won't be able to access your site from your LAN using the FQDN ([www.mydomain.com](www.mydomain.com)) unless your router or whatever DNS server your using points that for you.  Adjusting the clients hosts file gets around this issue.

---

### Post by seizart on 2010-12-17
Ok thanks

So is there anything i should know about this file hosts?

should i just add the line at the end of the file?

something like that ?

192.168.0.197 mydomain.org

Thnaks

---

### Post by arrrghhh on 2010-12-17
Yup, you got it.

```
127.0.0.1     hosting.gmodules.com
``` is what I have for an entry in my hosts file.  Not sure if you need all those spaces (in my hosts file it's 1 tab...), I think it's just for readability.

---

### Post by seizart on 2010-12-17
So i did it
And i have access to my website but still only from outside my network

i need to access my website from a computer inside my network with the public mydomain.com adress...

Is it just not possible ?

---

### Post by seizart on 2010-12-21
somebody has an idea?

---

### Post by arrrghhh on 2010-12-21
Please post your hosts file.  Must be something wrong within them...

---

### Post by seizart on 2011-01-21
> **arrrghhh said:**
> Please post your hosts file.  Must be something wrong within them...
here is my hosts file:

  GNU nano 2.2.4             Fichier : /etc/hosts                               

192.168.0.197   oldfixe-PC030A-ABA-SR1135CL-NA430       # Added by NetworkManag$
127.0.0.1       localhost.localdomain   localhost
::1     oldfixe-PC030A-ABA-SR1135CL-NA430       localhost6.localdomain6 localho$
127.0.1.1       oldfixe-PC030A-ABA-SR1135CL-NA430
192.168.0.197   videoconference.xxx.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


sorry for the delay i had to work on something else !

---

### Post by SeijiSensei on 2011-01-21
Can you ping "videoconference.xxx.com"?  Is the web server configured to serve pages for the virtual host videoconference.xxx.com?  Are you requesting "http://videoconference.xxx.com/"?

Just to make sure, people here are talking about the hosts file on the client you're using to connect, though you should have an identical entry for the "videoconference" host in the /etc/hosts file on the server, too.

---

### Post by arrrghhh on 2011-01-21
> **seizart said:**
> here is my hosts file:

```
GNU nano 2.2.4             Fichier : /etc/hosts                               

192.168.0.197   oldfixe-PC030A-ABA-SR1135CL-NA430       # Added by NetworkManag$
127.0.0.1       localhost.localdomain   localhost
::1     oldfixe-PC030A-ABA-SR1135CL-NA430       localhost6.localdomain6 localho$
127.0.1.1       oldfixe-PC030A-ABA-SR1135CL-NA430
192.168.0.197   videoconference.xxx.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


sorry for the delay i had to work on something else !

You have 192.168.0.197 mapped to two different hostnames...

---

### Post by seizart on 2011-01-25
I wish i could find something clear to configure my ubuntu !

I decided to reinstall everything but i keep missing something

all i want is to access my website from my external adress videoconference.xxx.com from my local network computer and from outside the network through internet.

it works well from outside my network but i can t make it work from my internal network after more than 5 try. 

Can somebody give me a clear answer on that, is it possible to use my external adress in local or i have to use the local adress in local (192.168.0.197)

Many thanks

---

### Post by arrrghhh on 2011-01-25
> **seizart said:**
> I wish i could find something clear to configure my ubuntu !

I decided to reinstall everything but i keep missing something

all i want is to access my website from my external adress videoconference.xxx.com from my local network computer and from outside the network through internet.

it works well from outside my network but i can t make it work from my internal network after more than 5 try. 

Can somebody give me a clear answer on that, is it possible to use my external adress in local or i have to use the local adress in local (192.168.0.197)

Many thanks

Read my last post.

---

### Post by Lloyd_mcse on 2011-01-25
If you are using a windows pc to connect to your domain/server, you can find the windows 7 host file - 

C:\Windows\System32\drivers\etc\

and add...

192.168.0.197    your-domain.com__[URL="http://www.your-domain.com"]
[/URL]

---

