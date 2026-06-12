---
title: "Alternative To Windows Server 2003 Packages"
date: 2008-09-03
forum: Server Platforms
---

### Post by anand_phulwani on 2008-09-03
Dear Forum Members,

God Day To All,

To Define I Am A Newbie To Ubuntu And I Am Trying To Replace
My Windows Server 2003 With Ubuntu Server 8.04 LTS.I Have The 
Following Things Installed On Windows Server 2003

1)DNS Server
2)DHCP Server
3)Print Server
4)File Server
5)ISA Server

So I Got My Ubunutu Server Ready,Installed The Following

1)Ubuntu Desktop
2)Samba Server(Took A Lot Of Time) For File Sharing

I Have Looked Over A Range Of DNS And DHCP Server's Available
**QUES1)Can Anyone Advice Me The Server That Can Be Configured With A GUI**

I Am Already Having FireStarter On My List

**QUES 2)Need Advice As An Alternative To ISA Server NAT Version**

Which Has The Following Capabilites
1)Can Be Configured Through GUI
2)Allow/Deny Policies With Respective To Different Users.
3)Allow/Deny Policies With Respective To Time Shifts
4)Allow/Deny Policies With Respective To Domains/Sub-Domains/URL's.
5)Allow/Deny Policies With Respective To Protocols And Ports.

Please Advice,And Thanks In Advance,

With Kind Regards,
Anand

---

### Post by cariboo on 2008-09-03
> 1)DNS Server
2)DHCP Server
3)Print Server

There are two ways to set this up, in a terminal type:

```
sudo tasksel
```

And select dns and printer servers, dhcp gets installed along with dns.

Install synaptic package manager then edit-->mark packages by task (not sure if adept has this ability).

Instead of firestarter try gufw it is available here:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

To configure most of these service editing the configurations file is the way to get things done. In most cases there isn't a gui anyway.

Just fyi the ubuntu server is designed to run headless and should be accessed remotely, you don't need a monitor and keyboard connected to the system.

If you do need a gui to set things up I would suggest webmin, a web based server administration suite. have a look here:

[http://www.webmin.com/](http://www.webmin.com/)

Try out the demo and see if it will fill your needs.

Jim

---

### Post by anand_phulwani on 2008-09-03
Dear Jim/Members,
Thanks For The Reply.

I Already Had Info About Webmin,Installed And Checked It Out,
But It Includes Squid Proxy Which Is A Proxy Server,
I Prefer NAT with Security,I Had A Look At Firewall Builder
And It Appears This Is What I Need,
Can You Look Into This And Advice Me Whether It Is Something
Which Would Be Reliable Or If Possible Suggest Something Similar

Thanks,
With Regards,
Anand

---

