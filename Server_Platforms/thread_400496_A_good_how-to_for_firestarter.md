---
title: "A good how-to for firestarter"
date: 2007-04-03
forum: Server Platforms
---

### Post by ShirishAg75 on 2007-04-03
Hi all,
       I am looking for a good how-to on firestarter if not something fantastic as a flash video/tutorial of zonealarm [http://download.zonelabs.com/bin/media/flash/clientTutorial/overview.html](http://download.zonelabs.com/bin/media/flash/clientTutorial/overview.html) . I have read the FAQ on fs-security.com & have become none the wiser. 
        So here is what I want to do, use firestarter so all my services, i.e. ktorrent, browser, gaim, download manager. I am also using a router+modem and no networks so do not need DHCP. 
       If somebody has already written a nice tutorial then link please. Its frustrating not finding a single nicely written tutorial for lay users to use firestarter.

---

### Post by HeyItsMatt on 2007-04-03
> **shirishag75 said:**
> Hi all,
       I am looking for a good how-to on firestarter if not something fantastic as a flash video/tutorial of zonealarm [http://download.zonelabs.com/bin/media/flash/clientTutorial/overview.html](http://download.zonelabs.com/bin/media/flash/clientTutorial/overview.html) . I have read the FAQ on fs-security.com & have become none the wiser. 
        So here is what I want to do, use firestarter so all my services, i.e. ktorrent, browser, gaim, download manager. I am also using a router+modem and no networks so do not need DHCP. 
       If somebody has already written a nice tutorial then link please. Its frustrating not finding a single nicely written tutorial for lay users to use firestarter.

Hey, I feel your pain.  I'm an Ubuntu newbie, and as much as I am liking it there seems to be a lack of nice, central "here's how to do it, newbie!" Linux-related tutorials.

I know you said you read the FAQ but have you read the Firestarter documentation?  [http://www.fs-security.com/docs.php]("http://www.fs-security.com/docs.php")
Starting on this page in particular I found it got more useful:
[http://www.fs-security.com/docs/events-page.php]("http://www.fs-security.com/docs/events-page.php")

From what I understand, Firestarter is basically just a GUI interface to the firewall that comes installed with your Ubuntu installation called "IPtables".  When you make rules in Firestarter, it applies the rules to the "IPtables" firewall, which remain even if you turn the Firestarter interface off.

By default, Firestarter blocks all connections coming from the internet to your computer, and allows any connections that you make from your computer to the internet.  If you select the "policy" tab on the Firestarter GUI, you can see an "Editing" option where you can choose to view your outbound or inbound traffic policy.  You can add a rule to either one by right-clicking in the correct area, clicking "add rule", and then adding the info needed.

The only thing that I had some issues with using Firestarter was BitTorrent - right now I use KTorrent, and in KTorrent it lists a default port that it uses, which I have added to my inbound connections policy in Firestarter.  This seems to work pretty well (amazing how long it took me just to get that simple thing down).  Having a router makes it more complicated - you either have to add rules in your router that forward ports to your computer, or use UPnP to have those rules set up for you, but then that's not really related to Firestarter.

---

### Post by huygens on 2007-04-03
If you follow the wizard of firestarter, and allow inbound connection for some services and host you trust. Then the protection given by firestarter for your home desktop is enough :-)

A guide for firestarter would be: install it, launch it, follow the wizard and that's it ;-)

To open a service, you open firestarter and go in the Policy tab. Right click in the Allow service area, and create a new rule. Apply the policy with the toolbar button once done.

If you want help on how to specify a particular policy rule. You can always ask, I'm not sure I would be able to answer complex configuration, but for standard one I should ;-)

---

