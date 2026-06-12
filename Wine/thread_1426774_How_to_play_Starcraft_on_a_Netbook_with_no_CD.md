---
title: "How to play Starcraft on a Netbook with no CD"
date: 2010-03-10
forum: Wine
---

### Post by *Azrael* on 2010-03-10
[SIZE=4]_**UNR 9.10: How to get Star Craft/Brood War running on a Netbook with no CD**_[/SIZE]

[FONT=Verdana][SIZE=2]**Equipment Used:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]HP Netbook Mini[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]USB CDROM Drive[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Star Craft CD[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Brood Wars CD[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]**OS: **[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]Ubuntu Netbook Remix 9.10 (UNR 9.10)[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]**Software Used**:[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]WINE (Installed from Ubuntu Software Centre on UNR 9.10)[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]**Note: **[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]I understand that Netbooks do not come with a CD-Rom drive. However, I bought an old 'My Box' USB drive equipped with a CD/DVD Rom at a yard sale for $5.00. It has served me well ever since.  [/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]If you do not have this type of CD/DVD Rom, I understand your frustration. I am confident that a similar device can be purchased from a computer store.  [/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]With that said, should you not be willing to purchase one (which I consider a must for any netbook owner). You may consider trying a work-around using one of the many ISO clients for UNR 9.10 (like GMount-iso).  [/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]On a desktop with a CD-ROM, create the ISO images of the Starcraft and Brood War CDs (using code listed below). Then put them on a USB stick and transfer them to your netbook. Mount and install them using ISO software (GMount-iso) into WINE. You can also use the ISO of Brood War you created later in this tutorial, by placing it in the suggested folder. (You will understand later...)  [/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]_**How to Run Star Craft and Brood War on a Netbook**_[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**Step 1:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Install WINE from Ubuntu Software Centre onto you netbook.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**Step 2:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Plug in your USB CD-ROM, and install Star Craft using WINE. Then install Brood Wars using WINE. (Leave Brood War CD in the drive.)[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**Step 3:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Restart the computer.  [/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]**Step 4:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Open up the Terminal to create an ISO of the Brood War CD, Code is as follows: (Note: name and computer are variables and will be replaced by your computers settings on your machine)  [/SIZE][/FONT]
 
[FONT=Courier New, monospace][SIZE=2]name@computer:~$ dd if=/dev/cdrom of=$HOME/BROODWAR.iso bs=64k[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Output should look like this when finished:[/SIZE][/FONT]
 
 [FONT=Courier New, monospace][SIZE=2]    9931+1 records in[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]    9931+1 records out[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]    650844160 bytes (651 MB) copied, 258.054 s, 2.5 MB/s[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**Step 5:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Create the directory to mount the ISO in:[/SIZE][/FONT]
 
 [FONT=Courier New, monospace][SIZE=2]    name@computer:~$ mkdir ~/virtualdrive[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]Then:[/SIZE][/FONT]

 [FONT=Courier New, monospace][SIZE=2]    name@computer:~$ mkdir ~/virtualdrive/Drive0[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**Step 7:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Mount the ISO to that directory:[/SIZE][/FONT]
 
[FONT=Courier New, monospace][SIZE=2]    name@computer:~$ sudo mount -o loop BROODWAR.iso ~/virtualdrive/Drive0[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Enter your password to complete the mount, output looks like this:[/SIZE][/FONT]
 
[FONT=Courier New, monospace][SIZE=2]    [sudo] password for name:[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Exit Terminal.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**Step 8: **[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]Unplug your  USB CD-Rom Drive from your Machine.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**Step 9:**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]Go to WINE Menu and clicking on *Configure Wine*.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Click on the *Drives* tab.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Click *Add*. (to add a new drive)[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Click on the new drive *letter* that popped up.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Click on *Show Advanced*.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]In the *Path* box write:[/SIZE][/FONT]

 [FONT=Times New Roman, serif][SIZE=3][FONT=Courier New, monospace][SIZE=2]    /home/name/virtualdrive/Drive0[/SIZE][/FONT]        [/SIZE][/FONT] 

 [FONT=Verdana][SIZE=2](where 'name' is in this path, put in your user name. Just like in the Terminal)[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]In the *Type* box, select CD-ROM[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]Within the area marked *Label and Serial Number*, in the *Manually Assign *field put a [FONT=Courier New]0[/FONT].[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]Check the box marked *Show dot files*.[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]Click *Apply*.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]Go to the Audio Tab. [/SIZE][/FONT] 
 
 [FONT=Verdana][SIZE=2]WINE will then tell you something to the effect of “no sound driver detected” or something like that. This is fine, wait a few seconds and it will create some default settings based on the sound requirements of the netbook. Do not change anything. [/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Click* Apply*.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]*Exit* Configure Wine.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]Click on the *Star Craft -Brood* Wars Icon in the WINE menu.[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Play Star Craft Brood Wars, and _enjoy it_.[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Cheers,[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]- Azrael
[/SIZE][/FONT]

---

### Post by Kartel on 2010-03-11
In the past, the problem I had with doing a sudo mount on an iso is that it would be gone after a reboot and I didn't really want to have to redo it every time.

What I ultimately did was I downloaded the installer from the blizzard website. As long as you have a valid product key, you can register it to a a blizzard store account and download the game it's for (and re-download in the future if need be). Since it's a downloaded version to begin with, it does not expect there to be a cd and will never ask for one. I've found this to be SO much more convenient than dealing with discs. I did the same for Diablo II as well.

I did have trouble getting the blizzard downloader to work with wine though (had to use Windows via virtualbox, though I assume it is do-able in wine).

Just a thought..

---

### Post by *Azrael* on 2010-03-12
That's an interesting way of doing it. I can understand the annoyance of constantly having to mount the CD image. 

However, as you mentioned, you had issues making the Blizzard loader work with Wine. That aside, you managed to make it work in Virtualbox (via windows). Which is great. But it does sound a little more labor intensive. With having to install virtualbox, then a windows OS. But it would work, and you have a windows environment to play with, so I can see the benifits. 
  
I assume I could write a executable script to mount the ISO. That would save time in terminal.

* I came up with this metheod in an attempt to keep it as lean as possible, as it is running on a netbook. *

---

