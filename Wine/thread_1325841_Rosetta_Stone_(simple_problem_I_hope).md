---
title: "Rosetta Stone (simple problem I hope)"
date: 2009-11-13
forum: Wine
---

### Post by ExSuSEusr on 2009-11-13
All,

Got my Rosetta Stone installed through WINE just fine.  It runs great (so far), but the problem is it's not detecting the language disk in the CD Rom.  WINE "sees" a D drive (CD ROM), but the program is not "seeing" it.

Any ideas?

This is what I am getting...

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x1549e0, filter=0x84e9d4,flags=0x00000001),
    returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x87e9c8): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x87e958): stub
fixme:service:EnumServicesStatusW 0x154ba0 type=30 state=3 (nil) 0 0x87e7e8 0x87e7f4 0x87e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x87e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x1549d0,(nil)): stub
wine: could not load L"C:\\windows\\system32\\rosetta.exe": Module not found

I'm not understanding the problem.  I am using 9.10 and the latest wine version.  Wine sees the drive but the program tells me "no language package detected"

---

### Post by ExSuSEusr on 2009-11-13
Ok I got it working.

This is what I did since I know there are other people who might be having the same problem.

I am using Wine 1.1.31 and Ubuntu 9.10

1.  Using WINE the install is pretty easy.  Just pop in the disk and install with WINE.  Straight forward.
2.  Install Gmount.iso from the Synaptic Package Manager.
3. Create a folder in your "Documents" folder or where ever.  I called mine "
Languages."
4. Create a folder within the newly created folder for each of your languages.  I called mine "French" and "Spanish."
5. Either copy the entire contents of your respective disk(s) to their folder(s) or the iso images of the language disks.
6.  Create a folder in the folder you created in step 3.  Call it whatever.
7.  Using Gmount.iso which will be found in your "Systems Tools" tab in your "Applications" tab set the path of the iso image to your iso image from step 5.
8.  Set the path of "Mount Point" to the folder you created in step 6.
9. Click "Mount"
10. Start Rosetta Stone.

It will show all your languages and works just fine - at least it did for me.

If anyone has a "better" way or easier way please share...

I hope this helps...

---

### Post by RazorV on 2009-11-23
Okay,  I think I did exactly what you said to do  but I would like to recap because RS still can't find the language packs (I'm running wine 1.1.31 and Ubuntu 9.10)

I created a folder in the DOCUMENTS folder called LANGUAGES
(/DOCUMENTS/LANGUAGES)

Then I created another folder as you indicated called GERMAN in the LANGUAGE folder
(/DOCUMENTS/LANGUAGES/GERMAN)

Then I copied the .iso file for German 1, 2, 3 into /DOCUMENTS/LANGUAGES/GERMAN

Then I Created another folder in /DOCUMENTS/LANGUAGE called MOUNT as you inidicted in step 6.  
(/DOCUMENTS/LANGUAGES/MOUNT

So basically I have 2 folders in the LANGUAGE folder - 'GERMAN' and 'MOUNT'

Using Gmount.iso i Mounted the GERMAN1 language pack .iso file located in '/DOCUMENTS/LANGUAGES/GERMAN/Rosetta Stone V3 - German L1.iso'

The Mount Point I set to /DOCUMENTS/LANGUAGES/MOUNT

I launch RS thru Wine and go to add a language and it still cannot find the image or CD to install the language.

Any clue to what I'm doing wrong?

thanks if you can help.

Greg

---

### Post by RazorV on 2009-11-23
Okay here is the EASY Answer for you

After you mount the .ISO file according to ExSuSEusr instructions.  You MUST go to Applications/WINE/Configure WINE

Click on the DRIVES tab
Then Add a drive - mine was E:
Then BROWSE to where the MOUNT location was.  
   Mine was '/home/gheidt/Documents/Languages/RosettaLP/'

Now what you have done is told WINE there is actually a Physical/Virtural Drive call E: that points to the mounted ISO image.  Rosetta Stone will now find the Language Pack and install.  

Hope this helps.

---

### Post by babusar on 2010-02-06
Thank you, that works perfectly!

---

### Post by diesel59 on 2010-02-16
Thanks to all for the help it is much appreciated.  

This was the last step in the ladder after playing around for a couple of hours with wine/rosetta stone configuration.  Thanks again to all the posters and the fantastic Ubuntu community!!!  (I am running Rosetta Stone 3.45, Ubuntu 9.10, and Wine 1.1.38)

---

