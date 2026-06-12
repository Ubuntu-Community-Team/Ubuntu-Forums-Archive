---
title: "Ubuntu Server - SMS server tools- DA BOMB!"
date: 2009-01-24
forum: Server Platforms
---

### Post by majikins on 2009-01-24
Hi

Just wanted to post this in case it helps someone else.

I had to set-up a server for a small organisation that needed, file and print, internet gateway and collaboration services.  I was seriously considering SME server as its dead easy to setup for what I need but they run on ancient kernels which was not conducive for various reasons one of which, the usb 3G modem could not work reliably.

So...got the latest server cd, loaded with Ebox after reading the punting by others on the forum.

Sidenote - Ebox package is broken via repositories for Intrepid.  This is very distressing - its actually listed in launchpad and I can't understand why the maintenance team would still keep it in the repositories if it is known to be broken - especially if its meant for server use.
Anyways I changed the sources.list file to reflect the ebox sites repository and got it to work.

Ebox so far seems to be doing the job I need it to do - the forums reflect some problems I have not come across yet and I hope it stays that way.  The impression I get is that it isn't quite production quality yet - unlike tried and tested SME Server.

Right - my next hurdle was to get the 3G modem to work reliably.  As the device is recognised by the kernel properly, all I needed was pppconfig and editing the /etc/ppp/options file to uncomment persistant and demand.
Then I added a cron job in root stop and start the modem once a day early in the morning.   Our network does not like the modem to be on continuously for ever and a day!:(

Next one - remote support requires some fancy footwork.  Here in South Africa, the ISP's and networks do their best to hamper our efforts to get the job done painlessly.  The 3G modem on the server is firewalled on the network side - allows no incoming traffic.  So cannot ssh in.  I am on the move all the time and most of my internet connectivity is via 3G modem too.  Fortunately the network has allowed an APN which provides a dynamic public IP that is not restricted.  However the downside to this is that port scanning etc counts towards your cap - which is obscenely expensive here.

So what I have done was read up on reverse ssh.  My basic idea is to reverse ssh from the server to my laptop via the 3G cards. I know needed the server to establish a connection to me on demand to an IP which changes on every connection to the network.  Hmmmmmmm...

Enter SMS server Tools.  What I have done is get sms tools to monitor incoming sms's via its GSM module, screen the messages for my number, and upon receipt executes a script on the content which includes my current IP and establishes the ssh connection.

Remote support established! :guitar:

Now all I do is establish a connection via the unrestricted apn via a ppp profile where-ever I am.

I just discovered SMS tools and am blown away with the potential of how it can help an adminstrator. There is a module which supports Nagios.  Everyone has an old phone lying around somewhere.

Anyways - hopes this helps someone.

Cheers 

Kudos to opensource, Linus, ubuntu etc etc.

---

### Post by majikins on 2009-03-14
update.

smstools in the repositories has an issue with sms monitoring.

The way that I got around that was to establish a screen session which runs smsd -s.
I have scripts which start on reboot and monitor the session.

Now sms's are processed reliably.

I have also used ssh to establish a ssh tunnel so that I can remote desktop to any client on the remote lan.

ssh user@remoteserver -L port_to_be_used_on_your_pc:ip_of_client_on_remotelan:port_of_clients_application

The above command means that your are using the remote server's access to the remote lan to "redirect" traffic from the remote pc to your pc.

Now the remote pc can accessed like so:

rdesktop localhost:port_to_be_used_on_your_pc

Remote support made easy!

---

