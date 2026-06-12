---
title: "Unable to get Elastic ip"
date: 2010-10-30
forum: Ubuntu Cloud and Juju
---

### Post by Chauhan Ankit on 2010-10-30
Hello all,
I have installed uec... one system is cloud,storage,walrus controller. second sysem is node controller,both on LAN. During installation i put the ip address range as 192.168.0.0-192.168.255.255. I am using Elastic fox and windows xp to manage server. But when i tried to run image of Lucid-Lynx downloaded from image store.... it says not available resources....try to use private address. On unchecking the public address, i was able to run the image...status 'running', but no elastic ip. Plz provide solutions for two things
1> How i connect to that running instance. I have already created the key pairs...for name "cloud". In instance tab when i try to connect to instance it asks for the key... 
[B]Which key i have to put there??
-> they key which i have created myself....for name "cloud", file named 'cloud.pem'
-> the key which i get on downloading credentials
-> or the AWS key shown in the admin panel of uec, under button 'show keys'
[/B]I have already opened the ports for ssh,rdp,http....under the security groups
2> I want to connect to cloud instances....Lucid-lynx here,directly by browser....How can i really perform that....is it really necessary to have elastic ip for this purpose??
:( 
Solve my problems guys....Thanks

---

### Post by wcorey on 2010-10-30
> **Chauhan Ankit said:**
> Hello all,
I have installed uec... one system is cloud,storage,walrus controller. second sysem is node controller,both on LAN. During installation i put the ip address range as 192.168.0.0-192.168.255.255. I am using Elastic fox and windows xp to manage server. But when i tried to run image of Lucid-Lynx downloaded from image store.... it says not available resources....try to use private address. On unchecking the public address, i was able to run the image...status 'running', but no elastic ip. Plz provide solutions for two things
1> How i connect to that running instance. I have already created the key pairs...for name "cloud". In instance tab when i try to connect to instance it asks for the key... 
[B]Which key i have to put there??
-> they key which i have created myself....for name "cloud", file named 'cloud.pem'
-> the key which i get on downloading credentials
-> or the AWS key shown in the admin panel of uec, under button 'show keys'
[/B]I have already opened the ports for ssh,rdp,http....under the security groups
2> I want to connect to cloud instances....Lucid-lynx here,directly by browser....How can i really perform that....is it really necessary to have elastic ip for this purpose??
:( 
Solve my problems guys....Thanks


Well, first of all I think you may have collided the elastic ip addresses right on top of the range of ip addresses your router is using. This does not appear to work and, if you think about it, it can't work as the router you plug your computer into say, 192.168.0.1-192.168.0.255 is where the ipaddress of machines you plug into your router are assigned. What I did, for instance, is assigned 192.168.0.100-192.168.0.199 as this is a range you'll likely never use and 255 is broadcast address so you can'/shouldn't use that anyway. 

Second, and I had more trouble with this on UEC 2.0 than I did on 1.0. Before you start an instance be sure to perform the folowing:

1	uecadmin@client1:~$ cd ~/.euca
2	[email]uecadmin@client1:~/.euca[/email]$ source eucarc
3	uecadmin@client1:~$ euca-add-keypair mykey > mykey.priv
4	uecadmin@client1:~$ chmod 600 mykey.priv

basically that is your home dir. From this point forward use -k mykey as your key and be sure elasticfox sees that as the keypair.

Third....bag ElasticFox for the time being, it will just confuse things and you won't know if a problem is with EF configuration or UEC configuration.

If you can't start an instance and ssh into it via cmd line it likely will never work via EF.

Fourth.... And this is, I believe, the route of my problem is. The assigned elastic ip address is only valid on the machine which assigned the ip address. Just, by way of some background. With UEC 1.0 I had a second machine configured as the NC and my normal desktop as the CC, SC, etc (everything other than the NC). So I could shell into my started instances, when they started Tomcat I could point to it with FF and life was good...right up until the elastic IP disappeared. I believe this was because the router owned that range and the different network manager in a Desktop might have been behaving far differently than what would be managing the ip addresses on the CC. So for UEC 2.0 I got a THIRD machine to be the CC, SC etc. I carved out the range of ip addresses I mentioned to you and that works perfectly from the new machine which is the CC. However, my desktop has no clue what 192.168.0.100 resolves to and so I can not reach the image from my desktop machine. 

Perhaps the answer lies in giving the CC (cluster1) a different subnet to assign ip addresses from like 192.168.1.100-199. Then add the address of the CC to /etc/resolv.conf. That may work. I added the second nameserver to resolv.conf but it doesn't seem to work. So I either maybe have to reboot or it is because it is the same subnet as everything else. 

So if you do what I suggested, that should get you farther than you are right now.

good luck

PS the show keys / secret key in the url is what you need to provide to ElasticFox for the credentials.
   the machine that assigned the elastic IP is the cluster controller. SO if you ssh to it and then use the Elastic IP it will work. That does, however beg the question of what good it is because from there you can use the private ip address. Elastic is supposed to be visible on your lan, or certainly the subnet. But, as I said, this is the thrust of my issue.

[https://help.ubuntu.com/10.10/serverguide/C/uec.html](https://help.ubuntu.com/10.10/serverguide/C/uec.html)

---

