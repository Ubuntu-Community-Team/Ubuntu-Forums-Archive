---
title: "VMWare Converter to resize client: SO close yet sooooo far"
date: 2008-06-22
forum: Virtualisation
---

### Post by bluewhale on 2008-06-22
I have a test rig at home that I'm using to, well, test an idea I read about. Here I believe. 

I have a number of 8 gig VMWare clients that need to grow. A number of people have suggested running VMWare Converter and resizing the client partition while going through the Converter wizard.  It works well until I try to find a place to put the new, converted client. 

For this instance I'm bumping it from 8 gigs to 11 gigs and renaming it. 

The problem is the converter is run from within the XP client.

     PC itself is Ubuntu 8.04
     VMWare Server 1.06
     Multiple VM clients, however this one is a throw away W2K install

The Converter Import Wizard ( used to export the "PC"... not import it )  :???::confused:   allows you to place the new, larger client on a network connection. Sadly I'm new to VMWare, to Ubuntu and to Macs. ( been busy lately :rolleyes:  )  From the XP VM client I can see the subnet all systems are using, however I can't get access to store files there. Have tried on the Mac Mini and will hold for now as I don't want to mess up the firewall/make a mistake to allow access from the web. 

I'm wondering if my choice during the install of VMWare Server was incorrect? The one where we decide whether to allow ... host only networking??  I also see that the VMWare host in Ubuntu is set by default to use SSL for Console communications with 'this host'.  Is this relevant? 

I Believe I need to open a share from the Ubuntu host to the VMWare XP Client..  Securely. ( secure from my router and the world beyond it )  

Does anyone have a suggestion?

---

### Post by bluewhale on 2008-07-05
Well, I finally answered my own Q.  

If you are puzzled about resizing VMWare partitions take a look here :


[http://www.cutawaysecurity.com/blog/archives/88](http://www.cutawaysecurity.com/blog/archives/88)


It does not use VMConverter, but it does work. After resizing I went to 


[http://vmware-land.com/Resizing_Virtual_Disks.html](http://vmware-land.com/Resizing_Virtual_Disks.html)


to learn about GParted.  Hope it doesn't take you as long as it took me to resize your partition :lolflag:

---

