---
title: "Simple VPN Feasibility"
date: 2008-12-19
forum: Server Platforms
---

### Post by borahshadow on 2008-12-19
HI.

I'll quickly introduce my scenario to give some background.

I take care of a simple home file server for my family. Currently it runs Dapper with LAMP, Samba and ClamAv installed with the root partition on an old 6GB Hdd(I think) and then 2 250GB drives mirrored in RAID 1. The LAMP is mainly for website testing it does not have port 80 forwarded to it. It is basically isolated from the outside internet. Samba is basically the only access to the files in order to solve some file permission issues. ClamAv is to scan for Windows viruses as the majority of the house runs Windows.

Ok ever since Hardy came out I wanted to upgrade the server to Hardy. Mainly to get a tickless kernel and a newer version of PHP. I have put it off until now as Christmas Break is now starting and I think I have time to finally perform the upgrade.

There have been several times that I have wanted access to files on the server from our cabin or a relatives house. Now my sister is moving out to go to college and does not want to take a copy of every file she might need with her.

Now to my question...
How hard would it be to set up a VPN (probably openvpn) to the server so that we don't have to take a copy of every file with us, but only the most important ones.
Also what are the security consequences of adding something like a VPN. Will it require many security measures or can I still just go along happily with just keeping up on the security updates and minor log watching etc.

Last note I run Kubuntu, Most of the rest of our computers run XP and my sister runs Vista. (I know unfortunate)

Thanks

---

### Post by koenn on 2008-12-20
openvpn should be OK.

I happen to be looking into a simple openvpn config over the weekend, and from what I've seen so far it's easy to set up and does exactly what you want.
It's pretty secure by itself so you don't need any additional precautions, except for the fact that your remote hosts (like your sister's PC) will have access to the server and possibly to the network around it, so whatever goes wrong there might affect your server's/network's security. Therefore you should worry about security on the openvpn clients rather than the server.

There's an excellent howto here : [http://openvpn.net/index.php/documentation/howto.html](http://openvpn.net/index.php/documentation/howto.html)

openvpn apparently also runs on Windows, so that's covered. You'll probably have to look into some NAT/port forwarding and dealing with dynamic addresses as well.

---

### Post by windependence on 2008-12-22
I can confirm OpenVPN is very solid. We just implemented OpenVPN for a client of ours that has 7-10 road warriors and they love it. 

One thing I should mention though is that we tried using UDP as the protocol but your lines have o be really clean. TCP works great and with LZW compression turned on it's quite fast and stable. I wasn't sure how we would scale because they only have about 500kb of bandwidth left after the phone system, but they have at times all hit the network simultaneously and there were no problems whatsoever.

Good luck!

-Tim

---

### Post by neomaximus2k on 2008-12-22
I'm also looking into a similar feature but for business use instead, I have several clients who would benefit from exchange and domain servers for their business but dont want to pay the stupid costs associated with a server.  I managed to pick up a quad core 2.1 server with 250Gb HDD and then upgraded the memory from 512kb to 4Gb all for £200 which is an ideal server for most small business users.

I should be setting up this small business server today at home so once ubuntu is installed and running i'll let you know how well it went!

Well so far I have installed openvpn and thats about it the link shown isn't for ubuntu and when you come to configure you cant :(


Well after much messing I managed to get so far

```
apt-get openvpn
```
then
```
cd /usr/share/doc/openvon/examples/easy-rsa/2.0
```
now you need to edit your vars file, i use nano as VI does my head in, you need to change the following
```

KEY_COUNTRY
KEY_PROVINCE
KEY_CITY
KEY_ORG
KEY_EMAIL

```
Ok now this part wasn't explained, you must source the vars file...
```
source ./vars
```
now we can start!!
```

./clean-all
./build-ca

```
Enter your certificate details here

now we build the server key
```
./build-key-server your.server.name.com
```
Answer yes when asked to sign and import to the database

now i'm stuck at present, I have create key passwords instead of the suggested method
```
./build-key-pass username
```
type in a password and again type in the details for the certificate like you did before and sign and import

---

### Post by borahshadow on 2008-12-22
Thanks everybody. This looks like good info.
I'm going to worry first about just getting the server working on the local network just like it was. Then I can add openvpn capability once it is up and functioning. 

I will probably post back here when the time comes to actually install the vpn as I will likely need some explanation on something.:)

Thanks

EDIT: Actually I just glanced at the openvpn howto on their site and already have a question :p. 
I want this simple as can be and saw the link for the static key setup I thought that sounds good, but it said only one client and one server. Is there no way to have 2-3 clients with a static key?

---

### Post by windependence on 2008-12-22
I currently have one set up with 10 clients. You have to generate keys for each client and they should be generated on the same machine. I would suggest generating a bunch of keys for future client use when you set it up. If you need help just post here in the forums or PM me.

There is also a GUI client for Windows including support for <ugh> Vista.

-Tim

---

### Post by samosamo on 2008-12-22
Anyone who doesn't install webmin on a server is insane.

That said, anyone who doesn't install webmin's openvpn plugin on a vpn server is even more insane.

Webmin plugin, after asking for a few pieces of info, will auto configure your server.  Then it will auto generate your client keys.  Then after asking for a few pieces of info it will auto generate client config using those keys.  Then you're done.

---

### Post by neomaximus2k on 2008-12-23
from what I understand webmin has been removed from ubuntu

---

### Post by borahshadow on 2009-01-02
Ok my server is now functioning to a point that I feel it is time to tackle an openvpn installation.

I looked around on the internet and got a little overwhelmed by the amount of information that was there. I think that I want a static key setup for simplicity's sake. However the [_**Static key mini-howto**_]("http://openvpn.net/index.php/documentation/miscellaneous/static-key-mini-howto.html") seems to assume that openvpn is already installed. If I just ```
sudo apt-get install openvpn
``` then am I ready to follow the rest of that tutorial?
On further examination I'm not sure that that tutorial is what I need as it only seems to allow one client. What do I need to do to have 3-4 clients?

To handle my dynamic IP from my ISP I'll probably have to set up a dnydns account right?

@samosamo Before I upgraded I had webmin installed and quite frankly I hardly ever used it.  However if you can provide some more details about how it configures the server I might take a look at installing it for that reason. However it is not in the repositories so I'd have to install from an unofficial source right? I'd rather not have to do that as then it won't update for security updates with the rest of the system and could break upon a full system update.  I will keep an open mind though if you can just tell me more about it.

---

### Post by cariboo on 2009-01-02
You can get the deb directly from the [source]("http://webmin.com"). The only thing is, is when there is a new version you have to manually update.

Jim

---

### Post by windependence on 2009-01-02
Some stuff that may help you:

[http://www.batcom-it.net/?p=30](http://www.batcom-it.net/?p=30)

[http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu)

[http://www.thebakershome.net/?q=node/56](http://www.thebakershome.net/?q=node/56)

[http://www.packtpub.com/page/OpenVPN:_Building_and_Integrating_Virtual_Private_Networks_Table_of_Contents](http://www.packtpub.com/page/OpenVPN:_Building_and_Integrating_Virtual_Private_Networks_Table_of_Contents)

[http://www.terminal23.net/2007/08/openvpn_20_on_ubuntu_704.html](http://www.terminal23.net/2007/08/openvpn_20_on_ubuntu_704.html)

There is more out there, and personally I think the easiest way to do this is to set up a pfsense box which has OpenVPN built in and configure it from there. You also get a nice firewall while you're at it.

If you need help, post here and I'll see what I can do.

-Tim

---

### Post by windependence on 2009-01-02
> **cariboo907 said:**
> You can get the deb directly from the [source]("http://webmin.com"). The only thing is, is when there is a new version you have to manually update.

Jim

Jim, what version is in the repos? he may not have to upgrade to the newest version. I think I'm running one or two versions back and I even have support for Vista.

-Tim

---

### Post by koenn on 2009-01-02
the 'static key' setup is pretty straightforward, I don't think it's worth setting up webmin just for that. (here are some notes : [http://users.telenet.be/mydotcom/howto/linux/openvpn.htm](http://users.telenet.be/mydotcom/howto/linux/openvpn.htm) )

apt-get install openvpn (on both server and client) is all you need. 
For more than 1 client apparently you'd have to set up a PKI, and you may need to install the openssl package (suggested by openvpn). On the other hand, apparently windependence knows how to set up multiple clients, maybe ask him. I've never done anything else but a single point-to-point.

---

### Post by HermanAB on 2009-01-02
Hmm, it sounds to me that you only want a casual (ad-hoc) connection.  OpenSSH is better for that and will allow you to do anything.  A server without SSH is inconceivable to me.

Using SSH to transfer files is as simple as typing sftp://ipaddress into the Nautilus or Konqueror address box.

Hope that helps!

Herman

---

### Post by borahshadow on 2009-01-02
> **HermanAB said:**
> Hmm, it sounds to me that you only want a casual (ad-hoc) connection.  OpenSSH is better for that and will allow you to do anything.  A server without SSH is inconceivable to me.

Using SSH to transfer files is as simple as typing sftp://ipaddress into the Nautilus or Konqueror address box.

Hope that helps!

Herman

How would that work for the windows clients?

---

### Post by HermanAB on 2009-01-02
For Windows, you can use Filezilla client.  It can do SFTP:
[http://filezilla-project.org/](http://filezilla-project.org/)

It works like a charm and you probably want SSH for remote management of the server anyway.  It is the only thing I use.

Cheers,

Herman

---

### Post by borahshadow on 2009-01-02
OK that sounds great. I already have ssh set up. However will it allow access to the samba shares or will it directly access the files?

---

### Post by borahshadow on 2009-01-03
Well I tried this [http://www.blisstonia.com/eolson/notes/smboverssh.php]("http://www.blisstonia.com/eolson/notes/smboverssh.php") but it seems that vista has a problem with no reasonable workaround. Too bad my sister uses vista. I'll have to figure out something else for her so I might as well just use a vpn for everybody.

---

### Post by Nott32 on 2009-01-03
Wouldn't Hamachi be the easiest solution?

---

### Post by windependence on 2009-01-03
> **borahshadow said:**
> How would that work for the windows clients?

You can also use WinSCP. It has a nicer interface IMHO, but I'm glad Hermann brought up sftp because many people are not aware of how easy this is, and it's secure as well without setting up an ftp server.

I think FreeNX would work for you as well. 

-Tim

---

### Post by neomaximus2k on 2009-01-03
> **borahshadow said:**
> Ok my server is now functioning to a point that I feel it is time to tackle an openvpn installation.

I looked around on the internet and got a little overwhelmed by the amount of information that was there. I think that I want a static key setup for simplicity's sake. However the [_**Static key mini-howto**_]("http://openvpn.net/index.php/documentation/miscellaneous/static-key-mini-howto.html") seems to assume that openvpn is already installed. If I just ```
sudo apt-get install openvpn
``` then am I ready to follow the rest of that tutorial?
On further examination I'm not sure that that tutorial is what I need as it only seems to allow one client. What do I need to do to have 3-4 clients?

To handle my dynamic IP from my ISP I'll probably have to set up a dnydns account right?

@samosamo Before I upgraded I had webmin installed and quite frankly I hardly ever used it.  However if you can provide some more details about how it configures the server I might take a look at installing it for that reason. However it is not in the repositories so I'd have to install from an unofficial source right? I'd rather not have to do that as then it won't update for security updates with the rest of the system and could break upon a full system update.  I will keep an open mind though if you can just tell me more about it.

In short yes just follow these instructions

```
apt-get install openvpn
```
That will install then
```
cd /usr/share/doc/openvon/examples/easy-rsa/2.0
```
now you need to edit your vars file, i use nano as VI does my head in, you need to change the following
```
KEY_COUNTRY
KEY_PROVINCE
KEY_CITY
KEY_ORG
KEY_EMAIL
```
Now you need to source the files, you may not need to do this but you should just incase
```
source ./vars
```
Now time to configure!
```
./clean-all
./build-cap
```
enter your certificate details and then we setup the server key
```
./build-key-server server
```
Answer yes when asked to sign and import to the database

This is as far as I got as I wanted to dial in from windows systems and never figured out which method I needed, everywhere I looked said to install the OpenVPN client onto windows but that isn't an option I need to use the built in system, I figured it would need to be the key-pass method but i never got it working let me know how you get on.

As for multiple clients, when you complete the certificate for a single client just do it again but with a different client name :) i'd create around 10 or more just to be safe!

As for webmin I use it a lot to manage the SAMBA shares, makes it a little easier than ssh into server and manually changing the conf file, and then restart samba with the etc/init.d command :(

I did just find this, its the module for webmin to manage openvpn so might give that a go next week
[http://www.openit.it/index.php/openit_en/software_libero/openvpnadmin](http://www.openit.it/index.php/openit_en/software_libero/openvpnadmin)

---

### Post by koenn on 2009-01-03
> **neomaximus2k said:**
> In short yes just follow these instructions

Aren't these instructions to set up the PKI infrastructure ? The OP is still considering to go with static keys, in which case a PKI isn't necessary.

As for multiple vpn's while still using static keys : I think it might be possible to start the openvpn server multiple times with a different configuration file, and since the static key file is referenced in the config file, you might thus start multiple instances each with a different key, which could maybe allow multiple clients to connect to it, each using its own key, corresponding to the key of one of the instances.
I think that's worth a shot. you might have to specify a different port for each instance, but that's only a minor issue. 
No guarantee, strictly speculation.

---

### Post by albinootje on 2009-01-03
> **samosamo said:**
> Anyone who doesn't install webmin on a server is insane. 

That depends.
Some years I've used webmin with the samba module, it wasn't so great after all.
Apart from that I prefer to be able (and continue to learn) to edit my configuration files myself, which is especially handy when there's a sudden network or boot problem.

---

### Post by borahshadow on 2009-01-03
Wow thanks for all the replies everybody.

I'm reluctant to use something like SCP or SFTP. The reason is that for permissions reasons I prefer to only access the files over samba. I know that makes things like this more complicated but it ensures that the permissions are always acceptable for access over samba.

The only reason that I wanted to use a static key was to keep it simple. I'd be fine with a PKI setup as long as it is reasonably simple (good step by step instructions will suffice).

I'm not sure that Hamachi it the right thing for me either because from what I could see it is a third party thing and looked windows based. However I didn't study it in detail.

FreeNX appears to be something like VNC for remote viewing of the screen but I could be wrong.


So basically it appears to me that VPN is still the best bet but static keys might not be.  The instructions that neomaximus2k posted look good but missing the end. They look similar to [_this link_]("http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu") that windependence posted. So far that tutorial looks the most promising of the ones I've seen.

@neomaximus2k I don't think you can use openvpn with the built in windows vpn software as they use a different vpn technology.

---

### Post by windependence on 2009-01-03
You are correct, the Windows VPN software is an IPSEC client and OpenVPN is an SSL VPN. 

Really, the simplest way for you to do this is to set up a gateway box for your network, it can be any old box you have around and run the pfsense web gui on it. Then, in the web GUI there is a simple to follow setup page just for VPN. Take a look at this document to see how easy it is:

[http://pfsense.nsa.co.il/tutorials/openvpn/pfsense-ovpn.pdf](http://pfsense.nsa.co.il/tutorials/openvpn/pfsense-ovpn.pdf)

This article is from 2006 but it works perfectly and is very easy to follow. Even if you're not going to use pfsense, it will help you generate the correct certificates and give you some understanding of how it works. Below are some more good tutorials.

[http://doc.pfsense.org/index.php/VPN_Capability_OpenVPN](http://doc.pfsense.org/index.php/VPN_Capability_OpenVPN)
[http://www.mdmmc.com/atarione/computers/pfsense/](http://www.mdmmc.com/atarione/computers/pfsense/)

You don't need to run multiple instances of OpenVPN to run multiple clients, you just need to use a new  unique client key for each client you set up. On the client will be a server key, a client key, and a client certificate. The server key lets the server know that the client is authorized to access it, the client key authenticates the client and the certificate lets the server know it is a trusted machine. These three go on the client box in your key directory. Setup of your server keys is well explained in all the tutorials I posted. Good Luck!

-Tim

---

### Post by koenn on 2009-01-03
> **windependence said:**
> 
You don't need to run multiple instances of OpenVPN to run multiple clients, you just need to use a new  unique client key for each client you set up. On the client will be a server key, a client key, and a client certificate. The server key lets the server know that the client is authorized to access it, the client key authenticates the client and the certificate lets the server know it is a trusted machine. These three go on the client box in your key directory. 

I suggested the 'multiple instances' as a (possible ?) way to use those so-called "static keys" while still allowing for multiple clients. These static keys are actually a shared secret, so I assumed it might work if for every client, there's a server instance with an identical key.

This is not the same as the public key authentication, which is the canonical way of working with multiple openvpn clients.

---

### Post by windependence on 2009-01-03
I wasn't criticizing you at all for your suggestion, just pointing out that you don't have to do it that way. :)

I am using PKI but through the pfsense interface. I have attached an image to show that. I know he doesn't have a gateway box, but IMHO it's much easier and safer to have the VPN server on a separate box.

-Tim

---

### Post by koenn on 2009-01-03
> **windependence said:**
> I wasn't criticizing you at all for your suggestion, just pointing out that you don't have to do it that way. :)

That's OK, i didn't take it is critisism, i though maybe you didn't realize I was suggesting an alternative. :)

---

### Post by neomaximus2k on 2009-01-15
so are we saying you cant get the windows vpn to talk to open vpn?

---

### Post by windependence on 2009-01-17
> **neomaximus2k said:**
> so are we saying you cant get the windows vpn to talk to open vpn?

Well, as far as I know the Windows client is IPSEC based, however, OpenVPN has it's own Windoze client.

-Tim

---

### Post by borahshadow on 2009-01-31
Ok everybody sorry that I kinda disappeared for a while there. I had some more pressing issues to deal with. I have decided that I am fine with a PKI setup. It seems the simplest way to get multiple clients connected. 

   Now I am trying to decide whether to use a routed or bridged VPN.  The openvpn documentation recommends use of a routed vpn unless a bridged VPN is specifically needed.  I found 2 tutorials that seem like good tutorials but they use bridged. This makes me lean towards using a bridged VPN. Also another plus (but not a necessity) is that for the windows clients Network Neighborhood will work over a bridged network but won't with routed.

  The other thing that I'm wondering about is... Should I change the network to a less common subnet?  Currently we are using the very common 192.168.0.0 255.255.255.0 Would it be good for me to change it to something like 192.168.12.0 255.255.255.0 or should I change it to something even more random like 10.12.55.0 255.255.255.0?

   And just to make sure that I understand this right... I will configure the server with a range of IP addresses that it can assign to the clients right? so I can configure my router to DCHP addresses X.X.X.65 - X.X.X.245 and then let open VPN have X.X.X.246 - X.X.X.254 right?

 Ps. The two tutorials that seem to be the best (IMO) are [https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN") and [http://www.thebakershome.net/openvpn_tutorial]("http://www.thebakershome.net/openvpn_tutorial")

---

