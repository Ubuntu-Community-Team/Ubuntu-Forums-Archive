---
title: "No broadcast for my dns"
date: 2006-08-31
forum: Server Platforms
---

### Post by larka06 on 2006-08-31
I have read this forum and many others trying to figure out why my DNS server does not broadcast.  I have went to popularity-contest and found that it is just for Debian packages. I am lost on how to get the dns to broadcast and become the dominate server.  I am using a hp xg833 with a 733mhz with 384megs of memory.  I can see my other machines broadcasting and a windows machine wins the contest.  Can anyone help me with this?:confused:

---

### Post by jimm on 2006-08-31
Hi,

I am a bit confused by your question...

Do you mean WINS? and Master Browser?

DNS doesnt broadcast and there are no browser elections...

Thanks,
James

---

### Post by larka06 on 2006-08-31
Ok It is a Ubuntu DNS.  I thought it had to broadcast and win the election.  Thank you

---

### Post by chrisfay on 2006-08-31
> I can see my other machines broadcasting and a windows machine wins the contest. 

What does this have to do with dns?

---

### Post by larka06 on 2006-08-31
Well I am not sure.  I was just guessing that was what is wrong with my dns not working.  I have followed two different setups now and still can not get it to work.  I will have to sit down and figure how to ask the right question.  I have setup my resolv.conf to look at my local net first then to go to the outside here is my resolv.conf
search robin.larka.rwr
nameserver 192.168.1.100
//
search hosts.bc1.bresnan.net
nameserver 69.146.17.3
nameserver 69.145.248.4
nameserver 69.146.17.2
I have also setup, exactly, the rest of the files as said in both of the HowTo's.  I am just stuck.

---

### Post by jimm on 2006-09-01
Hi,

Perhaps try explaining what it is you are trying to do? Are internet domain lookups broken i.e. ping [www.ubuntuforums.org](www.ubuntuforums.org) won't resolve. Or something on your internal network like ping myhomemachine.local wont work... or both

Start from first principles... forget the broadcast thing, what is it you want to be able to do?

Thanks,
James

---

### Post by larka06 on 2006-09-01
I have a home network of 6 machines, one xp, two 2000pro, and 3 linux.  I am setting up a www machine (linux), a samba machine (also linux), a mailserver (also linux). I would like to setup a domain for all of them.  I have the domain name of charken.com.  I have read that it is wise to only setup the http server under that name. I want to set them all up on a domain for learning purposes as well as experiance.  I also want to set the http machine up so it will be world reachable as well in the home network.  Naturally the samba machine will only be reachable to the home network.  If I can get all of this working I will then expand on the idea of having instant communication among the machines but, one step at a time.  The http machine is no problem I have done that for awhile now.  The samba I bought a good book on it so, it should not be a problem.  To get the DNS server working seems to be a problem.  There windows machines do not recongize the DNS machine as a domian server and from all I have read it also needs to be the source to the internet as well as the intranet. Oh! I am the linux person and the only one interested in this project.  Well they all want the samba machine to share files.  I have, in the past, setup the samba machine as s domein comtroller but wish to have my DNS machine be the source as well as the mail server. I almost forgot to tell you I can dig the DNS machine from any of my linux machines and all ssys ok.  I also used tomtom_erie guide this last time.  :grin:

---

### Post by chrisfay on 2006-09-01
> There windows machines do not recongize the DNS machine as a domian server

How do you know the windows machines are not using the DNS server you created?

Did you give your DNS server box a static IP? Did you input that IP into the DNS options in TCP/IP of each machine? If not, your machines will use the settings handed down from your router. 

> ..from all I have read it also needs to be the source to the internet as well as the intranet.

Again, not sure If I quite understand you here but your DNS server does not need to be the Gateway. You can use your router as the Gateway; just specify the IP of your router in the 'gateway' settings of your TCP/IP for all machines. 

> If I can get all of this working I will then expand on the idea of having instant communication among the machines but, one step at a time.

what?

> I have, in the past, setup the samba machine as s domein comtroller but wish to have my DNS machine be the source as well as the mail server.
Your mail server the source of what?


How do you have bind configured?

---

### Post by larka06 on 2006-09-02
Yes I have given my DNS server a static address.  As for the windows machine I have tried to set them up to use the DNS server according to the instructions. I also have set each machine to use the router gateway. I have put the address in the TCP/IP of the machines.  I also have followed the join a domain guide.  The first result is not connection to the internet.  The second result is there is no domain to join.  I will experiment with my other linux machines and see what happens while keeping a log of each step I make.  Hopefully this will allow you to see where I am making the mistake.
Thank you so much "chrisfay" for your time and effort towards helping me solve this.

---

