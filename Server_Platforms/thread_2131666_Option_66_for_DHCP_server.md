---
title: "Option 66 for DHCP server"
date: 2013-04-02
forum: Server Platforms
---

### Post by ejcoon on 2013-04-02
We are trying to connect to a PBX phone system and the vendor stated that we need to add option 66 to our DHCP server.  The line to add is: option 66 ascii sip:proxy@66.209.232.198:5062 .  How can I do that in Ubuntu 12.04?

Thanks

---

### Post by darkod on 2013-04-02
Your ubuntu is running the dhcp server, right? Is it the built in isc-dhcp-server or how ever it was called?

You can google about setting the option 66 for the dhcp server package you are using. If I'm not mistaken the 66 is a PXE boot server. Are you sure that line is correct for option 66? I guess the vendor knows what they are talking about.

---

### Post by jonobr on 2013-04-02
Hello

Option 66 (tftp server address) is usually used in conjunction with option 67 (filename)
You would add the option to your subnet declaration to allow it to use those parameters 

Here are the options 
[http://www.ipamworldwide.com/dhcp-options/isc-dhcpv4-options.html](http://www.ipamworldwide.com/dhcp-options/isc-dhcpv4-options.html)

In your declaration you should have something like

```
option tftp-server-name "ipaddressofserver";
```

You can test it by using a wireshark trace and filter DHCP messages,
in the options you should see the name or IP being handed back to the client.

---

### Post by koenn on 2013-04-02
> **darkod said:**
>  If I'm not mistaken the 66 is a PXE boot server. Are you sure that line is correct for option 66? I guess the vendor knows what they are talking about.

obviously the OP's question is about a config targetted at IP phones. So the correct value of that option will depend on the phones and the phone system the need to connect to, and this indeed can vary by vendor.

---

### Post by ejcoon on 2013-04-02
I have tried adding the line: option tftp-server-name 66.209.232.198:5062;

after saving and restarting the dhcp server it says it cannot start.  If I remove the line again and restart it will start.  Am I missing something?

Thanks for all the help so far.

---

### Post by darkod on 2013-04-02
Stupid question: Are you touching the correct dhcp server?

In most offices IP phones (voice) runs on separate VLAN which is like another separate physical LAN. You need this option in the dhcp serving the phones, in case you do have them separated from the data LAN.

Looks like you are entering the option correctly, but double check the syntax again if the dhcp is not starting after you add the option.

PS. Also double check with the vendor if you need the text "sip proxy" or similar in front or not. I fail to see what they are trying to do, I guess to connect the phones directly to their system/PBX without you having PBX on-site. Because that IP they gave you is public one.

---

### Post by koenn on 2013-04-02
> **ejcoon said:**
> I have tried adding the line: option tftp-server-name 66.209.232.198:5062;

after saving and restarting the dhcp server it says it cannot start.  If I remove the line again and restart it will start.  Am I missing something?


Sound like the dhcp server won't start because it trips over the confi file  - so that would suggest  a syntax error in the line in question. (your syslog or daemon log will probably have details about it)

Or troubleshoot by trial and error :
option 66 is a text typed option, maybe quoting it fixes things ?

---

### Post by koenn on 2013-04-02
> **darkod said:**
> 
PS. Also double check with the vendor if you need the text "sip proxy" or similar in front or not. I fail to see what they are trying to do, I guess to connect the phones directly to their system/PBX without you having PBX on-site. Because that IP they gave you is public one.

dhcp option 66 is just text, not necessarily a server name or ip address. But it does look like they're trying to just pass info to the phones and supposedly the phones will know what to do with it. - a vendor-specific dhcp option might have been a better way of implementing this. Apparently, other phone systems do something similar, eg look here : [http://www.3cx.com/sip-phones/dhcp-option-66/](http://www.3cx.com/sip-phones/dhcp-option-66/)

---

### Post by ejcoon on 2013-04-02
I will try the option with varying syntax.  Should it matter where in the config file it is inserted (ie in the {} for the scope)?  We are connecting across a dark fiber (layer 2 path) that connects to a VLAN with Layer 3 but the vendor failed to mention needing a DHCP server in place to complete the install.

Thanks again.

---

### Post by jonobr on 2013-04-03
Hello


Im not sure why the :5062 is in there.
tftp runs on port 69 UDP

Port 5060 is the SIP signalling port which sounds close to your 5062, but IM not sure why the port number is defined there.
Im pretty sure adding :5062 is stopping DHCP from starting

---

### Post by darkod on 2013-04-03
> **jonobr said:**
> Hello


Im not sure why the :5062 is in there.
tftp runs on port 69 UDP

Port 5060 is the SIP signalling port which sounds close to your 5062, but IM not sure why the port number is defined there.
Im pretty sure adding :5062 is stopping DHCP from starting

My guess would be they are trying to say to the phone(s): connect to ip 66.209.232.198 on port 5062. Many companies replace the default 5060 SIP port with another one, for protection I guess. It should work fine as long as you tell the phones where to look for the PBX. However, I'm not sure this should be done with the TFTP command.

I would expect the TFTP to only supply the TFTP server (and maybe a filename with option 67 as mentioned), and then inside the config file that the phone pulls from the TFTP you should put the port you want to use for the phone to communicate with the PBX.

I can't say I'm expert on this but this TFTP command looks weird to me.

On top of that, you need to be sure of the physical layout you have. For example, if your phones are somehow in another VLAN (through the dark fibre you mentioned), putting this option on your local network dhcp will not help you, even if you get the syntax right and the dhcp starts OK. You need the option on which ever dhcp server that is serving the phones.

---

### Post by ejcoon on 2013-04-03
The DHCP server I am configuring with the Option 66 is the one that serves the phones. They make the connection to the system through the fiber to the PBX on the other end. 

Thanks again for the help, still working on it.

---

### Post by darkod on 2013-04-03
How about a different type of test? Can you ping the PBX IP/hostname from your site using a machine in the phone VLAN?

Can you set a phone with manual settings just to see if it will register correctly on the PBX?

You did try the tftp option with only the IP without the port at the end right?

---

### Post by ejcoon on 2013-04-03
As far as I am aware, it is working now.  I had to change it to:
option tftp-server-name "66.209.232.198:5062";

this now makes the phone boot into the option 66.

Big Thanks to all the help here.

---

### Post by darkod on 2013-04-03
Great. :)

I think someone mentioned before putting the value in quotes.

---

### Post by jonobr on 2013-04-03
I think the reason is that phones like the cisco 79XX series phones can tftp their default boot params and basic configs from the PBX or other tftp server.
Im guessing the operation of the buttons, logo on the LCD screen, basic default feature set can all be centralized on a tftp server,
just a guess though

---

### Post by ejcoon on 2013-04-04
I was told today that tftp-server-name (option 66) does not work with the phones we are using (no idea why he said to use option 66 when it would not work).  I was told it needs to be sip:proxy@66.209.232.198:5062 instead.  Can I still do this in the DHCP server and if so, how?

Thanks

---

### Post by darkod on 2013-04-04
Try putting all of it as a value inside the quotes. But the option type still needs to be tftp-server-name which is equivalent to option 66 or they need to give you instructions of another dhcp option to use.

If we are not talking about a large number of phones, you might be better off doing things manually. If that is the address of the SIP server you can put that manually in most phones.

Autoconfiguration has it's benefits especially in large deployments, but sometimes it creates hassles too. In our small office the Thompsons we have boot much faster without TFTP on boot, and with manual configuration. Plus, I had the feeling the boot TFTP configuration wasn't even done properly by the previous administrator. It's a small number of phones so I just scrapped it all together, works great and boots faster with manual config.

EDIT PS. I was under the impression they know what they are talking about, but we might have been wrong. You said it yourself, first they say use that option, then they say it can't work. I am still wondering if that address is the PBX and the port it listens on. In that case, it shouldn't be in option 66 at all.

My logic is that you would use option 66 for IP phones to tell them where to download their config file from. And inside this config file you have the server address. You don't pass the PBX server to the phone with option 66 because the PBX usually is not booting the phone, especially not on port 5062. With option 66 you pass the TFTP/BOOTP server address. In this case it might be the same as the PBX but I'm starting to doubt that.

If you know how to configure that model manually, do a quick test. Go into the SIP config and put that IP and port for the server and proxy values. But you will also need a correct network config for the phone to be able to communicate in your LAN. See if that makes the phone work. If it does, that's the PBX address and I doubt it needs to be in option 66.

---

### Post by jonobr on 2013-04-04
Hello


I dont hold any hope for your vendor.
He seems a little lost.

I think what he may be asking you to do is to configure the phones to talk to their PBX, or, more likely he is giving you a proxy to talk to on the cloud.

The line he is giving you sip:proxy@66.209.232.198:5062 , seems more like the structure of a sip invite or registration packet rather then anything to do with DHCP or anything like that.

To make a call using sip, you send an invite.
The "to" address in the invite is <endpoint>@Sipserver/proxyIP:5060

Looking at your line
the ip address of the sip server is  66.209.232.198 - 
This belongs to [http://www.iquest.net/](http://www.iquest.net/) in Indiana.
It looks like these people are cloud services folks.

The port number is usually 5060 but they have given you 5062 which is ok, 

If you have a IP PBX server on your system, it looks as if they want you to point your sip server to theirs so they can handle your voice calls.

If you dont have a PBX server and your point all your phones to the "cloud" then that would also make sense.

Going back to the root of your problem, it looks as if they are trying to get you to setup something specific on your network IT infrastructure to enable voice services, but the guy may be a savvy Voip guy but not an IT guy.


I would recommend you ask what this 66.x.x.x server is,
Is it the registrar? IS it the Sip proxy/server? 
What is missing from the current setup that is stopping this from working?
What do I need to do my end to get this operational?
Explain what is required on the client to get this working and then we (you) could figure out how to configure or change or network to get this working.

The guy saying add this line to your "DHCP" is probably what you need now,
I would recommend he give you a technical description of what he needs from your IT infrastructure in order to get this working.
Then you can figure out how to get that done

---

### Post by ejcoon on 2013-04-04
I am in aggreement and very displeased.  After talks with them, they did not listen to what our connectivity was and are using cloud instead of the layer 2 fiber path.  All this was a waste of time.  Thanks for all the help.

---

### Post by jonobr on 2013-04-04
Hello,

It may not all be for naught,
What is your goal?
Implement a VoIP network or offload traffic from your Voip PBX to the IP cloud to avoid higher telephone charges?
If your trying to implement VoIP, you could make a stab at it yourself

---

