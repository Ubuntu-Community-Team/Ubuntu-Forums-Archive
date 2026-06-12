---
title: "System 76 - ubuntu 10.04 - panp7 - modem"
date: 2010-07-19
forum: System76 Support
---

### Post by Der_Kommissar on 2010-07-19
Recently my organization purchased quite a few of the Pangolin Performance laptops (panp7) to send to areas around the South Pacific.  I'm brand new to the world of Ubuntu, having only had a very limited exposure to LINUX about 10 years ago.  Please bear with me if I'm asking simple questions so far.  I really like Ubuntu in the month and a half I've been using it!

So... how the heck do I enable the modem?  I took a look at my "Ubuntu Unleashed" book and fiddled with the Network connections but I can't seem to find the magic button.  If I try to add a wired connection Ubuntu seems to think I mean Ethernet and doesn't give me the option for a modem.

Thanks in advance!

---

### Post by isantop on 2010-07-20
The modem in the PanP7 is not supported by Ubuntu, and we can't make it work. However, we have heard that several customers like [this](http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=3718719&sku=U13-4292&srkey=USRobotics%20USR5637) one, which works out of the box.

------INSTALLATION INSTRUCTIONS------
1. Insert an Ubuntu live CD.
2. Go to System > Administration > Software Sources and enable "CD ROM", click "Close" and then click "Reload."
3. Open a terminal (Applications > Accessories > Terminal) and run...

sudo apt-get install gnome-ppp

4. If you are running Ubuntu 9.10 or above, also run...

sudo apt-get remove modemmanager

5. Plug USB modem into a USB port of the computer and connect it to a telephone jack.
6. Go to System > Preferences > Main Menu and locate the Gnome PPP entry (it will be under Applications > Internet). Highlight Gnome PPP and click properties. Change the command to...
gksu "gnome-ppp" and click OK.
6. Go to Applications > Internet > Gnome PPP. You will be prompted for a password. Once Gnome-ppp opens, click the "Setup" button. Then click the "Detect" button. Most likely the settings will change to...

Device: /dev/ttyACM0
Type: Analog Modem

7. Click "Close."
8. Enter the username, password, and phone number for your dial-up service. Then click "Connect."

---

### Post by Eldera on 2010-07-20
isantop: please double check the link "this"
Thank you.

Edit: Link still isn't working.

Edit 2: Thanks for fixing the link

---

### Post by Der_Kommissar on 2010-07-21
Thank you for the reply, isantop.  I'm bummed that hardware on the machine isn't supported by the OS.  I'll have to check into getting modems sent to the folks on islands that don't have broadband access.  (The link is incorrect though)

---

### Post by isantop on 2010-07-21
The link is updated, and should be working.

---

### Post by Der_Kommissar on 2010-08-17
Finally got a USR5637 USB 56k modem to try out.  Isantop, your instructions worked perfectly.  Now I have to take some screen shots to add to that and send the modems to the far corners of the Pacific to the System76 machines we sent out.

I know modems aren't very prevalent these days, and the pangolin page doesn't say that the modem is supported, but it might be helpful for the small number of folks out there that need it to know that it's not supported by Ubuntu.

---

