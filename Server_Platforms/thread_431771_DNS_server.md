---
title: "DNS server"
date: 2007-05-03
forum: Server Platforms
---

### Post by kramerkeller on 2007-05-03
I am using an ubuntu tutorial I found online.  Below is says replace example.com with your domain name.  This might be a dumb question, but what is my domain name?  Also it says replace ns1 with the name of your DNS server.  Where do I find this?

// replace example.com with your domain name. do not forget the . after the domain name! 
// Also, replace ns1 with the name of your DNS server 

example.com. IN SOA ns1.example.com. admin.example.com. ( 

// Do not modify the following lines!
            2006081401 
            28800 
            3600 
            604800 
            38400 
) 
// Replace the following line as necessary: 
// ns1 = DNS Server name 
// mta = mail server name 
// example.com = domain name 
example.com. IN NS ns1.example.com. 
example.com. IN MX 10 mta.example.com. 

// Replace the IP address with the right IP addresses. 
www IN A 192.168.0.2 
mta IN A 192.168.0.3 
ns1 IN A 192.168.0.1

---

### Post by MJN on 2007-05-03
Don't take this the wrong way but if you don't know what your domain name is then you probably haven't got one!

As far as you providing services (e.g. website etc) to the Internet is concerned you need a publicly-accessible domain name - these usually come at a cost and are available from a million and one registrars. For example, mine is 'newtonnet.co.uk'.

It might be better for us to take a step back and ask what it is you're trying to achieve? The answer to this will likely dictate whether you need a domain name in the first place, and indeed whether you need to be running your own DNS server too.

Mathew

---

### Post by kramerkeller on 2007-05-03
I currently own two domain names.  I host 3 websites (one under a subdomain) on my home server.  They are available online and work fine.  (running a LAMP server)
 
I even have ftp access all set up and a number of other programs running.

However, I can't view my websites on the local network.  I can type in an IP and see one of the sites, but not the actual name, unless outside my local network.

I have been told I just have to set up some zone files.  However, it looks like I have to find out my ISP's dns server.  Create a local DNS server and forward all quieries not on the network to the isp.  So i know some of what is going on, just way short of enough I suppose.

So as to the domain name, I own two that point to my external address and port forward to my linux box which in turn resolves the names in apache with some virtual hosting.

I just want to be able to type in the name on my local network and resolve it.

---

### Post by twistedtwig on 2007-05-03
can you not type in the name of your sever?

I host a few on my server and can do servename.com

or subdom.servname.com

or hostedsite.com

just a thought not sure if it is right in your situaiton

---

### Post by nomb on 2007-05-03
Are you running firestarter?  What I had to do was under the incoming connection where you can choose to let in certian ips or hostnames I had to put

192.168.0.1/24

Then my computers on my lan were able to see the webpage hosted on my server locally.  But if you can ftp to that server locally that probably isn't the issue.

---

### Post by MJN on 2007-05-03
In that case you've answered your own question - your domain name is one of the three (if not all) that you're trying to access.

To be honest I'd take a step back from the planned 'solution' and find the real cause of the problem.

What setup have you got? A router sharing your Internet access to a LAN, and your server/clients sitting on it? How many machines?

Can you resolve your domain name from a LAN machine? (e.g. **dig [www.example.com]("http://www.example.com") A**) and, if so, presumably you're getting your public IP address?

If you are unable to connect your server via the public IP address then it could well be that your router doesn't support so-called 'NAT loopback' in which case I'd suggest simple adding entries for your domain names to /etc/hosts pointing to the local (private) address of the server e.g. **<192.168.0.50> [www.example.com]("http://www.example.com") example.com etc.etc.com**

This would need to be repeated for all your LAN machines (hence why I asked how many machines you have).

Unless you've got some reason to keep it secret what is your domain name? This would help enormously in confirming that everything is fine from the outside. Keeping it hidden throws too much doubt into the equation (for me at least).

Mathew

---

### Post by kramerkeller on 2007-05-03
Sorry, I should have been more specific.  I took a walk and cooled down.

Here is all the info.  My setup is a bit complicated I must admint

First off I have a netgear router i believe its r614
I also have an airport (for wireless connections)

My roomate has a windows desktop, a windows notebook, and an xbox
(3 computers)

I have a dual boot ubuntu/windows desktop and an iBook G4
(2 computers)

I also have an ubuntu server
(1 computer)

Because I have the airport plugged into the netgear router for wireless it sort of counts as one computer
(Somehow with my wireless router it works with the netgear router and I can ping any computer regardless of wireless or not)

My main website is createcandor.com.  It is hosted on my ubuntu server.  I use zone edit to forward createcandor.com to my external ip address.  My netgear router port forwards HTTP, SSH, and FTP to my ubuntu server located at 192.168.0.3

So total including the ubuntu server there are 6 or 7 computers if you count depending on wether the mac airport.

I also have kramerkeller.com you can go to it as well, but I am redoing the wordpress site so you won't see much.

I use virtual hosting in apache to differentiate incoming requests.  So it knows which site to output if you type in kramerkeller.com or createcandor.com

I can't type those names on any of the computers on my local network though and I would like to.

I know I can configure each computer to read the appropriate name, but I would like to have a local DNS as sometimes new computers are added and not added to the network.  My router has the ability to use different DNS servers.  For now I am just using my local machines with links to test everything then I will tackle the router (one variable at a time)

So I was hoping to have my router use the linux box as the dns server.  Then it would resolve the local addresses and send the rest of the address not in a zone file to my ip's DNS.

I might not know what I am talking about in that last part.  Essentially, if I type in createcandor.com on the local machines it would use the local dns server and then if that dns didn't have the name it would then go to the regular dns server my isp has.

Alright, I think that is everything.  Let me know if any of you need additional information.

---

### Post by MJN on 2007-05-03
Thanks for the extra details (that'll teach me!) - but before I digest it further we need to look a bit deeper into this as I still think your router won't allow you to play ball, specifically accessing your server via your public IP address like the rest of us on the 'outside' are doing....

The bottom line is can you connect to your website from a LAN machine with [http://65.31.216.226/](http://65.31.216.226/) but not [http://createcandor.com/](http://createcandor.com/)  ? If so, then that is significant with how you populate your DNS server (if you choose to have one) as it means the 'locally-served' records for your domains will need to be local (private) IP addresses whereas those to the rest of the world (via ZoneEdit's servers) will be public.

Otherwise, you simply need to configure a local DNS server and point your router to it. But then you're just back to square one and given there are a million-and-one HowTo's on the topic I'm wondering if I've misunderstood what it is you're trying to do? At the very least I'd choose another HowTo - the one you've quoted from sounds a bit naff (particularly given it's not explaining why everything is configured as it is).

Mathew

---

### Post by kramerkeller on 2007-05-03
I think that when I type createcandor.com externally, that request goes to zone edit.  Zone edit in turn points it to 
[http://65.31.216.226/](http://65.31.216.226/).  Any http request that goes to that address is then forwarded by my router to my local address and ubuntu server 192.168.0.3.

In my apache virtual host file it takes any request from 192.168.0.3 and given the name createcandor.com or kramerkeller.com it points to the correct folder.


I think on my internal network when I request a site it uses my ISP's DNS.  Then it hits createcandor.com and zone edit points it back to itselfl meaning my external address.  For some reason it can't "loopback" or whatever.  So it just says page not found.  I can go to 192.168.0.3 and it will give my default page or the first page listed in the virtual host.  So I can access one of my sites internally.  However, I can't type in the name to access the other sites.

So what I think I need to do is instead of having my router go to my ISP's DNS.  I need to go to a local DNS which looks for names in its zone and then it will use my router's DNS again or forward to all those main DNS serrver A - M or whatever.

This is really out of my depth.  I don't know how to do it, but I know it is possible.  My router has the ability to use a different DNS.  I figured I would just make my linux box the DNS.

---

### Post by kramerkeller on 2007-05-03
oh and yes, if I do dig createcandor.com

It gives me my external IP and the zoneedit ns9 and ns7

---

### Post by MJN on 2007-05-03
So, to confirm, you **can't** access [http://65.31.216.226/](http://65.31.216.226/) from within your LAN?

NAT loopback aside I'm not sure what the problem is - just set up a DNS server but choose a different HowTo given the one you've followed seemingly doesn't explain what it's trying to do.

Then point your router to use your server for its DNS.

Mathew

---

### Post by kramerkeller on 2007-05-03
on my LAN i cannot access [http://65.31.216.226/](http://65.31.216.226/)

because it is my external address

As to the how to's.  I have looked at tons of them.

I have not been able to make a DNS (server).  If I could I would.  Then I would have no problem.

---

### Post by MJN on 2007-05-03
> **kramerkeller said:**
> on my LAN i cannot access [http://65.31.216.226/](http://65.31.216.226/)

because it is my external address

It's because your router doesn't support NAT loopback. Mine does, but of course that's no help to you! I was just checking if yours did or didn't as this determines how your DNS should be populated - if it did support it then you'd have no need for an 'internal' DNS, period.

> As to the how to's.  I have looked at tons of them.

I have not been able to make a DNS (server).  If I could I would.  Then I would have no problem.I don't run a BIND DNS server myself so am not the best one to walk you through it but give it time and someone will surely be along to guide you through the steps.

Mathew

---

### Post by kramerkeller on 2007-05-03
Thanks for your help.  I will be messing around with bind the rest the day so hopefully Ill be lucky and get an expert.

---

