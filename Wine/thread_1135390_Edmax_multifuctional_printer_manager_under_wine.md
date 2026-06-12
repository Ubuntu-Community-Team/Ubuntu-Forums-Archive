---
title: "Edmax multifuctional printer manager under wine"
date: 2009-04-24
forum: Wine
---

### Post by chrisginger26 on 2009-04-24
Hi Guys 

I am currently moving my  home network to xubuntu/ubuntu/linux from windows/mac os.

I Have a PC in the lounge which is now set up and running mythbuntu 8.10, an eeepc (running xandros to get my wife to convert from mac os) and an imac 17inch 1.25ghz g4 in the kitchen which will eventualy run xubuntu.

So far I have the network setup and I can see all shares on all machines BUT I can only print when the imac is switched on.

The printer is not connected directly to the Imac it is connected to my BT Home Hub via an Edimax ps-1206mf print server and previously this was manager by a application in windows xp called mfp manager.

I have had various attempts at geting this app to run under wine the installer runs its course on the eeepc and gives various x11 warnings about failng to intialise windows firewall :0x80040134. I solved this by changing  wine configuration for this app to windows 98 and the software installed completely but would not see the server on the network. 

I also tryed installing the software on my mythbuntu box and that gave me the same result the mfp manager appears on the desktop but won't start and at the end of the installer it asked me to select a server but there were no servers to select just as with the eeepc.

My apologies for sounding a little vague! But my main aim for this post is to see if it is even possible to install this type of software through wine as it is kind of a semi driver/app? 

Can the server be reached through wine or is this beyond wine?

thanx again

chris

---

### Post by asdfoo on 2009-04-24
> **chrisginger26 said:**
> Hi Guys 

I am currently moving my  home network to xubuntu/ubuntu/linux from windows/mac os.

I Have a PC in the lounge which is now set up and running mythbuntu 8.10, an eeepc (running xandros to get my wife to convert from mac os) and an imac 17inch 1.25ghz g4 in the kitchen which will eventualy run xubuntu.

So far I have the network setup and I can see all shares on all machines BUT I can only print when the imac is switched on.

The printer is not connected directly to the Imac it is connected to my BT Home Hub via an Edimax ps-1206mf print server and previously this was manager by a application in windows xp called mfp manager.

I have had various attempts at geting this app to run under wine the installer runs its course on the eeepc and gives various x11 warnings about failng to intialise windows firewall :0x80040134. I solved this by changing  wine configuration for this app to windows 98 and the software installed completely but would not see the server on the network. 

I also tryed installing the software on my mythbuntu box and that gave me the same result the mfp manager appears on the desktop but won't start and at the end of the installer it asked me to select a server but there were no servers to select just as with the eeepc.

My apologies for sounding a little vague! But my main aim for this post is to see if it is even possible to install this type of software through wine as it is kind of a semi driver/app? 

Can the server be reached through wine or is this beyond wine?

thanx again

chris

which Wine version? Wine 1.1.20 is the newest. please try that. [http://winehq.org/download](http://winehq.org/download)

---

### Post by chrisginger26 on 2009-04-26
Hi asdfoo

I have checked in synaptic package manager and found I am running wine version1.0.1-0ubuntu3-int according to synaptic this is the latest version.

I also have wine tricks installed.

Is there another version and if so how do I install it??

after re-installing the setup.exe on my mythbox I have found that the two pieces of software for the server show up server manager and MFP Manager.

Server manager actualy works and  can find the server on the net work and alter its settings.

BUT the MFP manager will not start this gives several errors the first being

servoApp

SetupDiEnumDviceInterfaces()returns code:259

then 

ServoApp

Virtual Bus Driver not Loaded

then again after that

servoApp

SetupDiEnumDviceInterfaces()returns code:259

then I get 

servoApp

CreateEhciFile() returns INVALID_HANDLE_VALUE in DeleteEHCIHostController().

and then back to desktop.

Does this mean that I don't have the correct DLL's installed ?

Can wine run this type of app? (it connects the computer to the server so that the other functions of the printer i.e scanner etc can be used otherwise it is only a printer)

thanx again

chris

---

### Post by chrisginger26 on 2009-04-26
Hi Guys 

Just quick update have tryed running the app with applictions tab set to windows 98 mode but this dosen't make any difference.

Help please so don't want a windows partition !!!!!!!!!!


thanx again 

chris

---

### Post by asdfoo on 2009-04-26
> **chrisginger26 said:**
> Hi Guys 

Just quick update have tryed running the app with applictions tab set to windows 98 mode but this dosen't make any difference.

Help please so don't want a windows partition !!!!!!!!!!


thanx again 

chris

visit [http://winehq.org/download](http://winehq.org/download) to find the instructions for updating to the latest testing/beta release (hundreds of bug fixes since 1.0.1)

---

### Post by chrisginger26 on 2009-04-26
Hi asdfoo

I have followed the instructions and updated the mythbox to wine version 1.1.20 and I am still getting the same errors.

After looking on the EEEpc user forum I tryed winefile in termial and found the folder where my apps are stored MFPAgent.exe and MFPAdmin.exe and I tryed to load the files from there and I can run the server manager (MFPdmin.exe) and it sees the server over the network but I still can't run MFP manager (MFPAgent.exe) I get the same errors as the mythbox on the eeepc??

thanx again 

chris

---

### Post by chrisginger26 on 2009-04-26
Hi  guys 


Did a little searching around I think that this 
ServoApp 

Virtual Bus Driver not Loaded

 error is something to do with wine not finding the network adapter as when googled it refers this error to this page at microsoft 

[http://support.microsoft.com/kb/921440](http://support.microsoft.com/kb/921440)

am I shooting along the right lines is it not possible to run this software in wine?

thanx again

chris

---

### Post by asdfoo on 2009-04-26
> **chrisginger26 said:**
> Hi  guys 


Did a little searching around I think that this 
ServoApp 

Virtual Bus Driver not Loaded

 error is something to do with wine not finding the network adapter as when googled it refers this error to this page at microsoft 

[http://support.microsoft.com/kb/921440](http://support.microsoft.com/kb/921440)

am I shooting along the right lines is it not possible to run this software in wine?

thanx again

chris

Yeah, if it is trying to load a real device driver then that isn't supported by Wine yet... low priority until other more pressing things are working well.

---

### Post by chrisginger26 on 2009-04-27
Hi asdfoo

If this is the case and the software is trying to load a driver would this app work through the Ndis wrapper or is that not how that works?

Sorry I know this is the wrong place to post this actual question 

thanx again

chris

---

### Post by asdfoo on 2009-04-27
> **chrisginger26 said:**
> Hi asdfoo

If this is the case and the software is trying to load a driver would this app work through the Ndis wrapper or is that not how that works?

Sorry I know this is the wrong place to post this actual question 

thanx again

chris

people have talked about exploring ndiswrapper for various drivers, but at this stage there is no usable solution for Wine, sorry

---

### Post by the4thamigo_uk on 2009-09-26
I had the same problem and I have found a solution without the need to install any drivers.

(1) Open System->Administration->Printing
(2) On the 'Printer Configuration' window click New->Printer
(3) On the 'New Printer' window expand Network Printer->LPD/LPR Host or Printer
(4) Type the ip address into the 'Host' field
(5) Type 'lpt1' into the 'Queue' field Click Forward and wait
(6) On the 'Choose drivers' page ensure 'Select printer from database' is selected and find your printer in the list and click Forward

hope this helps...

---

