---
title: "Can a Guest OS conect to localhost only?"
date: 2010-10-04
forum: Virtualisation
---

### Post by MaxVK on 2010-10-04
Hi.

Iv just started to use VirtualBox to run Windows for web development testing, and I have it connecting to my Xampp localhost where I do my development.

The connection (using Bridging) works just fine, but Id like to know if there is a way for me to allow the guest OS to continue to connect to localhost but NOT to the internet?

Its simply about security. I don't want the guest OS visible to the internet while I'm testing in localhost, and I really don't want to have to install virus checkers etc on it.

I'm sure this can be done, but I just cant seem to work out where.

Any ideas would be much appreciated.

Cheers

Max

---

### Post by scrooge_74 on 2010-10-05
Instead of bridge mode you can use NAT mode, that way the Guest OS is behind your Host OS in its own network. You can browse the internet same as if you were behind a router/firewall

---

### Post by MaxVK on 2010-10-06
Thanks scrooge, but I was under the impression that NAT mode would allow connection to the internet but not localhost, which is the opposite to what I need. (localhost is via Xampp running on Ubuntu, testing in Windows via VM)

Perhaps Iv read something wrong though - Could you clarify for me please?

Cheers

Max

---

### Post by Stunts on 2010-10-06
Hi there.
On the virtual machine settings go to the network category.
Under "Adapter 1" - which is pretty much the only on you need for what you mentioned, change from "Bridged" or "NAT" to "Internal network". That will allow only connections to your localhost, and "keep the internet out".

Hope that helps.

---

### Post by MaxVK on 2010-10-06
Hmm thanks guys, but...

Neither method will connect to my Ubuntu localhost. Iv had a search around, but if the answers are there they are buried in technical network speak that I have no understanding of.

The 'Host only' network seems to be what I'm looking for, but it fails as well as NAT when it comes to connecting to localhost on Ubuntu. So far bridged is the only way Iv ever connected to anything from the guest XP VM.

Any help would be much appreciated, but please bear in mind that my idea of setting up a network is to plug in a router and let Ubuntu do its thing (worked first time so Iv never had cause to look at it!)

Cheers

Max

---

### Post by Stunts on 2010-10-06
OK, so here's another idea:
Setup a connection that can connect to both you host OS and the internet.
Then in the guest OS, go to Control Panel -> Internet Options;
Go to the "Connection" tab, and untick "Automatically detect settings";
Click "LAN settings" and tick "Use proxy server", and just make up an IP address that doesn't exist. (like 123.123.123.123).
Then click "advanced" and add the host IP address for the "Do not use proxy server for...".
This will make sure you can reach your host OS, but it will block everything else from the internet.
Hope that works this time.

---

### Post by MaxVK on 2010-10-06
I manged to work it out, but its a bit of a hack I'm afraid:

1) Networking for VM set to 'Host Only'
This creates a new adapter called vboxnet0

2) On the command line 'ifconfig vboxnet0'
This should give you a bunch of stuff, but in there somewhere is an IP address. Make a note of it.

3) I already had some settings in my internet options (control panel on the VM) so Ill put them here since Iv not changed them and everything is working!

Control Panel->Internet Options->Connections Tab->LAN Settings

Make sure both items in automatic configuration at the top are NOT checked then click 'Use a proxy server for your LAN'

Enter an imaginary address and click 'Advanced'

At the bottom of the next window, in the Exceptions panel, type the address that you got from part 2 (ifconfig vboxnet0)

Click all the okay buttons to get out.

4) In all browsers the Ubuntu localhost can be reached by:
http:// [IP from part 2]

None of the browsers can reach the internet, and I hope that the internet cant reach Windows, in any case the connection seems to be what I was trying to do.

Thanks for your help guys.

Max

---

### Post by Stunts on 2010-10-06
You're welcome, I'm glad you sorted it out.
Don't forget to mark the thread as solved.

---

