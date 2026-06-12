---
title: "samba browse list fails between vmhost and vms"
date: 2014-10-08
forum: Virtualisation
---

### Post by betchern0t on 2014-10-08
Hi,
     I have a KVM host running 14.04 trusty. I have two KVM vms running 12.04 and 14.04 respectively. Each of the three are running the native version of Samba for that ubuntu version. The host runs a bridged setup with the two VMs having their own static ip addresses on the same subnet as the host. Each of the three instances is also on the virtual .122 network. The two VMs provide the master browser on the windows network and only the VMs are listed. There are a few other computers on the network running samba in another workgroup and they are listed in smbtree and in nautilus. the Host is never listed. SMBtree from the host lists the view from the browse list and doesn't include itself. Sometimes it is out of date.

Things I have looked at :

1) brought the three smb.confs into line with each other

2) ensured using preferred browser etc and OS level that the host should get master browser - it never does

3) Setup Domain Master Browser and Local Master Browser in case it was acting like separate subnets.

4) disabling multicast routing treatment on the host bridge - I need this anyway for my webdav and upnp services

It looks to me like broadcast traffic is not happening between the VMs and the Host. 

Any ideas how to push this further?

Cheers Paul

---

### Post by TheFu on 2014-10-08
Please post all relevant network data:
* bridge status/settings
* routes
* ifconfig for each
* firewall data

BTW - why not use NFS for linux-to-linux file sharing?

---

### Post by bab1 on 2014-10-08
> **betchern0t said:**
> Hi,
     I have a KVM host running 14.04 trusty. I have two KVM vms running 12.04 and 14.04 respectively. Each of the three are running the native version of Samba for that ubuntu version. The host runs a bridged setup with the two VMs having their own static ip addresses on the same subnet as the host. Each of the three instances is also on the virtual .122 network. The two VMs provide the master browser on the windows network and only the VMs are listed. There are a few other computers on the network running samba in another workgroup and they are listed in smbtree and in nautilus. the Host is never listed. SMBtree from the host lists the view from the browse list and doesn't include itself. Sometimes it is out of date.

Things I have looked at :

1) brought the three smb.confs into line with each other

2) ensured using preferred browser etc and OS level that the host should get master browser - it never does

3) Setup Domain Master Browser and Local Master Browser in case it was acting like separate subnets.

4) disabling multicast routing treatment on the host bridge - I need this anyway for my webdav and upnp services

It looks to me like broadcast traffic is not happening between the VMs and the Host. 

Any ideas how to push this further?

Cheers Paul
Just a quick glance at what you have here.  You need to use a WINS server if you have hosts on separate networks.If not the browse list is discovered by broadcast (bcast).

---

### Post by betchern0t on 2014-10-08
Hi,
     thanks for the responses. All three are on the same two subnets. The requested information is below. There are no firewalls in place only the internet gateway (Nehemiah) which is running IPFire.

Three instances are:

Korah running 12.04 as a VM
Cain running 14.04 as a VM
Bildad running 14.04 as the KVM host

[IMG]http://www.singlespoon.org.au/m25/korah.png[/IMG]

[IMG]http://www.singlespoon.org.au/m25/cain.png[/IMG]

[IMG]http://www.singlespoon.org.au/m25/bildad2.png[/IMG]

[IMG]http://www.singlespoon.org.au/m25/bildad1.png[/IMG]

All instances can ping each other.

Many thanks in advance

Paul

[IMG]http://www.singlespoon.org.au/m25/bildad3.png[/IMG]

[IMG]http://www.singlespoon.org.au/m25/bildad4.png[/IMG]

---

### Post by bab1 on 2014-10-08
Simple enough.  Run Wireshark (tshark) or tcpdump to analyze the traffic between the various hosts in the network.  You can filter tshark captures by protocol.

---

### Post by betchern0t on 2014-10-08
Hi Bab1,
             the problem is the place to stand. All the traffic I am interested in will be inside the physical box Bildad across the bridge br0 etc. Since these are commandline only servers that only leaves tcpdump or is there something nicer?

Cheers Paul

---

### Post by betchern0t on 2014-10-09
It is always the simplest and stupidest things that get you. In this case the most probable cause was a hung nmbd. I used to understand all this stuff but I am a long way away from Windows now and it shows. Moral is to always restart Samba rather than smbd or nmbd by itself.

There was a question from bab1 as to why smb and not nfs. The real problem is the ubiquitousness of windows out there. We run a lot of android devices. Direct connecting android to linux now is a bit hit and miss - another culprit in a long list of companies who use linux and then break inter linux connectivity. We heavily use smb to pull files - books, movies and music to our phones and tablets. SMB tends to just work whereas webdav and MTP are flakey. MTP sometimes works. Webdav works on and off depending on the upgrade cycle of the two clients I am aware of.

Cheers Paul

---

### Post by TheFu on 2014-10-09
Glad it is solved.  The .122. network wasn't being used at all.  I delete that bridge - it was put there automatically by libvirt. It was flaky for a few years (maybe not anymore?), I prefer the manually created bridges in /etc/network/interfaces and use those.

I asked about NFS - mainly because there were only 3 Linux systems listed. NFS is more convenient for inter-Linux use than Samba for multi-user environments due to the permissions capabilities. It is also faster than CIFS in my experience.  But, you aren't wrong about CIFS being more prevalent.  

I know you didn't ask, but for sharing media to my android devices and playback devices around the house, the Plex Media Server at the center and DLNA clients and renderers around it make all that easy. For android, BubbleUPnP is nice and can download entire albums from Plex - on demand.  I ran cifs, xbmc for years before discovering plex ... wish I'd switched years ago.  The only downside to plex is it isn't F/LOSS - blob release but still free. I don't have a plex account, do not sign in and access media only on the local network. It is really slick.

For other needs, I use an sftp client. This means the traffic is encrypted and it means access from anywhere in the world is fine (key-based authentication only). There are sftp clients for every platform.

Basically the only time CIFS is used here is for Windows systems and only on the LAN (performance). Externally, WinSCP is used for sftp access.  ssh/scp/sftp rock.

MTP sucks. I'm forced to use it too, from time to time.

---

