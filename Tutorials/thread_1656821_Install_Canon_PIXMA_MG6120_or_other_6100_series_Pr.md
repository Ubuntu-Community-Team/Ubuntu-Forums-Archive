---
title: "Install Canon PIXMA MG6120 or other 6100 series Printer"
date: 2010-12-31
forum: Tutorials
---

### Post by antonyhand on 2010-12-31
I received the Canon MG6120 as a Christmas present and found that I could not install the printer nor scanner, after much searching I found the answers but hoped this would help. Go to...

[http://support-sg.canon-asia.com/?personal](http://support-sg.canon-asia.com/?personal)

Then select: -
Product category: Multifunctional Printers
Product Series: PIXMA
Model: PIXMA MG6170 (closest to 6120 but drive is for all 6100 series)
Document type: Drivers and Software

Hit Find...

Then either go through the pages or use the Sear within these results to search for linux and download the following two drivers to your computer.

[MG6100 series IJ Printer Driver Ver. 3.40 for **Linux** (debian **...**]("http://support-sg.canon-asia.com/contents/SG/EN/0100301802.html")                                                      MG6100 series IJ Printer Driver Ver. 3.40 for **Linux** (debian Packagearchive). **...** OS.
 **Linux**. Detail.                        Thank you for using the IJ Printer Driver for **Linux**. **...**  
support-sg.canon-asia.com/contents/SG/EN/0100301802.html[SIZE=-2][COLOR=#565656] - 80k[/COLOR][/SIZE][SIZE=-2][COLOR=#565656] - 2010-09-03

[/COLOR][/SIZE][MG6100 series ScanGear MP Ver. 1.60 for **Linux** (debian **...**]("http://support-sg.canon-asia.com/contents/SG/EN/0100303102.html")                                                      MG6100 series ScanGear MP Ver. 1.60 for **Linux** (debian Packagearchive). **...** OS. **Linux**.
 Detail. Thank                        you for using the ScanGear MP for **Linux**. **...**  
support-sg.canon-asia.com/contents/SG/EN/0100303102.html[SIZE=-2][COLOR=#565656] - 78k[/COLOR][/SIZE][SIZE=-2][COLOR=#565656] - 2010-09-03[/COLOR][/SIZE]
[SIZE=-2][COLOR=#565656]
[FONT=Arial][SIZE=2][COLOR=Black]Once downloaded Extract the files to a location where you can find them.
Then use "Places" to find the folders 
1) "cnijfilter-mg6100series-3.40-1-deb"
2) "scangearmp-mg6100series-1.60-1-deb" 

For each folder: -
1) open the [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][SIZE=-2][COLOR=#565656][FONT=Arial][SIZE=2][COLOR=Black]"packages" sub-folder
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][SIZE=-2][COLOR=#565656][FONT=Arial][SIZE=2][COLOR=Black]2) double click on the appropriate .deb file [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][SIZE=-2][COLOR=#565656][FONT=Arial][SIZE=2][COLOR=Black](386 or amd)[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][SIZE=-2][COLOR=#565656][FONT=Arial][SIZE=2][COLOR=Black] which will open the Ubuntu Software Center
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][SIZE=-2][COLOR=#565656][FONT=Arial][SIZE=2][COLOR=Black]3) Installing the "-common" file first and then the "-mg6100series" file. 

So you should have installed 4 total drivers.
You can now add the printer and scan (from GIMP only unfortunately) either via USB or via Network.

[/COLOR][/SIZE][/FONT]Good Luck
[/COLOR][/SIZE]

---

### Post by cb750rob on 2011-01-02
Good News thanks for the post. I have a mg6150 which works with these.

Just for info:

"You can now add the printer and scan (from GIMP only unfortunately) either via USB or via Network."

You don't need Gimp - if you launch scangearmp from a terminal or create a launcher on the desktop with that command you can launch the scanner utility - You may need to ask it to search for scanners if you are on a network tho.

Hope this helps

Regards 

Rob

---

### Post by antonyhand on 2011-01-03
Thanks, this makes it easier

---

### Post by glombool on 2011-01-11
I just set mine up using drivers from the following site:
[http://software.canon-europe.com/products/0010892.asp](http://software.canon-europe.com/products/0010892.asp)

The page will be for an "MG6140" but the drivers work just great for the 6120.  I have mine set up on a wireless network.

Download the drivers for the printer and for the scanner.  Inside the .tar archives, look for the files ending in deb.tar.gz.  Extract the files in this archive and run install.sh.

The printer should be listed in the printers list.
Scangearmg should find the scanner.

---

### Post by ziusudra on 2011-02-15
Thanks, it's working perfectly fine but ...
I can't change the resolution, I just have 600dpi, my printer (MG6130) should be able to print on 9600x2400dpi

Do you have the same problem ?

---

### Post by ziusudra on 2011-02-21
No one has a clue ?

---

### Post by beerfan on 2011-03-06
Note that the install script that comes with the print drivers doesn't seem to run in Karmic Koala. If you are unable to install using the script or simply don't want to use it then do the following. This assumes that the printer is set up as a network printer and not attached via USB.

1. Install the print drivers and the scangear drivers with the debs (double-click them).

2. Make sure the printer is turned on and run "scangearmp" from a terminal or from alt-f2.

3. Let the scangear app find the printer and note the mac address which is the string of numbers separated by dashes in parenthesis.

4. Go to System > Administration > Printing

5. Add a printer, select "Other", and enter the following in the device URI field, but using the numbers reported by the scangear: cnijnet:/00-11-22-33-44-55

6. Select "Canon" and then "MG6100" (note that it does not start with Pixma)

There is also a guide to install manually from the command line in the guide included with the download at [http://software.canon-europe.com/software/0040261.asp](http://software.canon-europe.com/software/0040261.asp) but perhaps these instructions will be easier for some.

Also note that the guide suggests that it may be necessary to install the printer on a windows system first or attached via USB before it will work in a network configuration with this driver.

---

### Post by Yann2 on 2011-03-18
I also have a number of issues:
* Impossible to print in grayscale - I only get RGB
* I can't find where to select the print quality...

Suggestions to any of those problems welcome!

---

### Post by Yann2 on 2011-03-18
OK replying to myself here: I'm having some success using this: [http://loginspires.livejournal.com/2033.html](http://loginspires.livejournal.com/2033.html)

I've got the grayscale to work (at least it prints gray when I select it and print a colour file, i hope it uses the right cartridges) - when selecting a different quality it doesnt want to print, so I guess I need to work a bit more on it. So glad the grayscale works at least :)

EDIT: Damn it might be my eyes at fault but printing in lower quality (the quality setting seem to work, I can see the quality difference and it takes longer to print higher quality) it seems that the grayscale setting does NOT work - as opposed to what is claimed on many blogs. Selecting it will indeed print in grayscale, but the small dots seem to be coloured, ie I believe it uses the colour cartridges. This is an issue :(

---

### Post by ashv3524 on 2011-03-26
Thanks to Yann2's advice, I was able to make grayscale and quality settings work. To get this to work for you in Lucid 10.04, first follow the original poster antonyhand's steps to install the MG6100 series printer drivers. If you choose all the defaults and do a network (wireless) install, you should have a printer called MG6100LAN in your System-> Administration-> Printing view. Also, you should have a file MG6100LAN.ppd in /etc/cups/ppd. Edit this PPD file and replace the following lines

```

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

```

with

```

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 300dpi
*Resolution 300dpi/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*ColorModel RGB16/RGB 16-bit: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 16>>setpagedevice"
*ColorModel Black/Grayscale Fast: "<</cupsColorOrder 0/cupsColorSpace 3/cupsCompression 0/cupsBitsPerColor 1>>setpagedevice"
*ColorModel Gray/Grayscale: "<</cupsColorOrder 0/cupsColorSpace 0/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 4
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Economy: "4"
*CloseUI: *CNQuality

*OpenUI *CNGrayscale/Grayscale: Boolean
*DefaultCNGrayscale: True
*CNGrayscale True/Yes: True
*CNGrayscale False/No: False
*CloseUI: *CNGrayscale


```

Save the edited PPD file and you should now be able to print in grayscale and economy (those have been set as defaults).

---

### Post by ashv3524 on 2011-03-26
These modifications to the PPD file should also work for the MG8120 printer.

---

### Post by ashv3524 on 2011-03-26
Also, after further experimentation, it is possible to control dithering etc. If you'd like to be able to control half-toning and colors & intensity, edit the PPD file further so that just after 

```

*CloseUI: *CNQuality

```add these lines

```

*UIConstraints: *CNQuality 4 *MediaType matte
*UIConstraints: *MediaType matte *CNQuality 4
*UIConstraints: *CNQuality 4 *MediaType glossypaper
*UIConstraints: *MediaType glossypaper *CNQuality 4
*UIConstraints: *CNQuality 4 *MediaType highres
*UIConstraints: *MediaType highres *CNQuality 4
*UIConstraints: *CNQuality 4 *MediaType postcard
*UIConstraints: *MediaType postcard *CNQuality 4
*UIConstraints: *CNQuality 2 *MediaType tshirt
*UIConstraints: *MediaType tshirt *CNQuality 2
*UIConstraints: *CNQuality 4 *MediaType tshirt
*UIConstraints: *MediaType tshirt *CNQuality 4
*UIConstraints: *CNQuality 4 *MediaType envelope
*UIConstraints: *MediaType envelope *CNQuality 4
*UIConstraints: *CNQuality 2 *MediaType otherphoto
*UIConstraints: *MediaType otherphoto *CNQuality 2
*UIConstraints: *CNQuality 4 *MediaType otherphoto
*UIConstraints: *MediaType otherphoto *CNQuality 4

*OpenUI *CNHalftoning/Halftoning: PickOne
*DefaultCNHalftoning: ed
*CNHalftoning ed/Error Diffusion: ed
*CNHalftoning pattern/Dither Pattern: pattern
*CloseUI: *CNHalftoning

*UIConstraints: *CNHalftoning pattern *MediaType matte
*UIConstraints: *MediaType matte *CNHalftoning pattern
*UIConstraints: *CNHalftoning pattern *MediaType glossypaper
*UIConstraints: *MediaType glossypaper *CNHalftoning pattern
*UIConstraints: *CNHalftoning pattern *MediaType highres
*UIConstraints: *MediaType highres *CNHalftoning pattern
*UIConstraints: *CNHalftoning pattern *MediaType ijpostcard
*UIConstraints: *MediaType ijpostcard *CNHalftoning pattern
*UIConstraints: *CNHalftoning pattern *MediaType postcard
*UIConstraints: *MediaType postcard *CNHalftoning pattern
*UIConstraints: *CNHalftoning pattern *MediaType tshirt
*UIConstraints: *MediaType tshirt *CNHalftoning pattern
*UIConstraints: *CNHalftoning pattern *MediaType envelope
*UIConstraints: *MediaType envelope *CNHalftoning pattern
*UIConstraints: *CNHalftoning pattern *MediaType otherphoto
*UIConstraints: *MediaType otherphoto *CNHalftoning pattern

*%------------------------------------------------------
*OpenGroup: Colors and Intensity
*%------------------------------------------------------

*OpenUI *CNRenderIntent/Vivid Photo: PickOne
*DefaultCNRenderIntent: photo
*CNRenderIntent photo/Photo: photo
*CNRenderIntent vivid/Vivid: vivid
*CloseUI: *CNRenderIntent

*OpenUI *CNBalanceC/Cyan: PickOne
*DefaultCNBalanceC: 0
*CNBalanceC -50/-50:-50
*CNBalanceC -40/-40:-40
*CNBalanceC -30/-30:-30
*CNBalanceC -20/-20:-20
*CNBalanceC -10/-10:-10
*CNBalanceC   0/-0-:0
*CNBalanceC 10/+10:+10
*CNBalanceC 20/+20:+20
*CNBalanceC 30/+30:+30
*CNBalanceC 40/+40:+40
*CNBalanceC 50/+50:+50
*CloseUI: *CNBalanceC

*OpenUI *CNBalanceM/Magenta: PickOne
*DefaultCNBalanceM: 0
*CNBalanceM -50/-50:-50
*CNBalanceM -40/-40:-40
*CNBalanceM -30/-30:-30
*CNBalanceM -20/-20:-20
*CNBalanceM -10/-10:-10
*CNBalanceM   0/-0-:0
*CNBalanceM 10/+10:+10
*CNBalanceM 20/+20:+20
*CNBalanceM 30/+30:+30
*CNBalanceM 40/+40:+40
*CNBalanceM 50/+50:+50
*CloseUI: *CNBalanceM

*OpenUI *CNBalanceY/Yellow: PickOne
*DefaultCNBalanceY: 0
*CNBalanceY -50/-50:-50
*CNBalanceY -40/-40:-40
*CNBalanceY -30/-30:-30
*CNBalanceY -20/-20:-20
*CNBalanceY -10/-10:-10
*CNBalanceY   0/-0-:0
*CNBalanceY 10/+10:+10
*CNBalanceY 20/+20:+20
*CNBalanceY 30/+30:+30
*CNBalanceY 40/+40:+40
*CNBalanceY 50/+50:+50
*CloseUI: *CNBalanceY

*OpenUI *CNDensity/Intensity: PickOne
*DefaultCNDensity: 0
*CNDensity -50/-50:-50
*CNDensity -40/-40:-40
*CNDensity -30/-30:-30
*CNDensity -20/-20:-20
*CNDensity -10/-10:-10
*CNDensity   0/-0-:0
*CNDensity 10/+10:+10
*CNDensity 20/+20:+20
*CNDensity 30/+30:+30
*CNDensity 40/+40:+40
*CNDensity 50/+50:+50
*CloseUI: *CNDensity

*OpenUI *CNContrast/Contrast: PickOne
*DefaultCNContrast: 0
*CNContrast -50/-50:-50
*CNContrast -40/-40:-40
*CNContrast -30/-30:-30
*CNContrast -20/-20:-20
*CNContrast -10/-10:-10
*CNContrast   0/-0-:0
*CNContrast 10/+10:+10
*CNContrast 20/+20:+20
*CNContrast 30/+30:+30
*CNContrast 40/+40:+40
*CNContrast 50/+50:+50
*CloseUI: *CNContrast

*OpenUI *CNGamma/Brightness: PickOne
*DefaultCNGamma: 1.8
*CNGamma 1.4/Light:  "1.4"
*CNGamma 1.8/Normal: "1.8"
*CNGamma 2.2/Dark:   "2.2"
*CloseUI: *CNGamma

*%------------------------------------------------------
*CloseGroup: Colors and Intensity
*%------------------------------------------------------

```

---

### Post by Yann2 on 2011-03-26
Hello ashv3524, thanks for your notes - am using your settings now. selecting grayscale everywhere and printing a test page in low quality and gray scale still prints the page in grayscale, but using RGB ink drops for me. Look very closely at your print, and check the colour of the ink drops in a "bright" area - I can clearly see red, greed and blue points, that amount to "gray" if looked from more than 30cms away. I'd be interested to know if you can notice that too.

---

### Post by Yann2 on 2011-03-26
Ok I've finally found my answer here: [http://www.howtofixcomputers.com/forums/printers/canon-ip4200-b-w-still-uses-color-6067.html](http://www.howtofixcomputers.com/forums/printers/canon-ip4200-b-w-still-uses-color-6067.html)

The reason why my printer was using colour inks to output grayscale was that I was printing in duplex mode. When printing grayscale in duplex mode it will use colour ink - when printing one-sided it will use black ink.

I can see printing one-sided that the grayscale setting does work. Weird eh - and fairly annoying (I was hoping to print long texts in b&w).

---

### Post by kay-man on 2011-03-30
This is on purpose, so maybe not so weird as it may seem. I read somewhere that it prints the first side using the pigment black ink, and the other side using the dye (color) inks. This has to do with the pigment ink taking less time to dry.

---

### Post by foxy123 on 2011-04-01
Is it possible to use it with the Simple Scan?

---

### Post by thenudehamster on 2011-05-29
I've been looking for this for what seems to be ages - thanks to all for the advice; my MG6150 is now at least reachable. Whether I'll find the same problems as others remains to be seen; greyscales won't worry me too much as I also have a duplexing laser which can take care of that for me but the information is at least worth having. 

I've flagged the driver installation problem to Canon, too, in case they do decide to rewrite the installer. 

What confused me as much as anything was that the Canon script worked perfectly on my bedroom box which is running 11.04 under X-fce (Xubuntu), so I guessed that the Unity interface must somehow be causing the problem, but it seems that some people running older releases are suffering too - unless they've just omitted to update their profile....

EDIT: Curiouser and curiouser, to misquote Alice. I've just installed the driver *with* the Canon script onto another machine indoors running 11.04 under Unity - and it went straight in with no trouble at all!

Sometimes I just HATE b****y computers!

---

### Post by Zerolux on 2011-06-08
Similar problems with the installer on my 2 pc's, the i386 wouldnt come up at all, but the x64 went first go....

Found that after installing the 2 .deb packages from each of the canon drivers, I extracted the MG6100LAN.ppd from the cnijnet filter source code and then simply pointed the driver search to that and bingo!

PS Natty doesnt seem to find the driver for this in its own database which is funny as others seem to have

J

---

### Post by Kaizoku001 on 2011-09-10
I install the drivers for a MG6130.
it seams to print well, but I can't figure out how to scan whit it.
GIMP dosen't give me any scan option,
and simple scan also can't find any source.

Any ideas

---

### Post by foxy123 on 2011-09-10
> **Kaizoku001 said:**
> I install the drivers for a MG6130.
it seams to print well, but I can't figure out how to scan whit it.
GIMP dosen't give me any scan option,
and simple scan also can't find any source.

Any ideas

you need to use scangearmp from the command line.

---

### Post by Kaizoku001 on 2011-09-10
> **foxy123 said:**
> you need to use scangearmp from the command line.

So I can't use it with other programs? 
If so I'm really bummed out. 
I tried out Ubuntu a few years ago and I had no problem scanning with my Canon MP 600. Couldn't Print to save my life with it, but I COULD SCAN.

why can't xsane or Gimp recognize it? after all I can print with them.

########################

Just realized I can scan with GIMP
Go to File-creat-Scangear Mp

But I still can get xsane to work, GIMP is good for scaning 1 file, but sometimes I have to scan a whole book. Saving one file at a time is hell.

---

### Post by loseby on 2012-05-16
a lot of help here but what I need it set it up as a network printer, printer is a MG650

My setup is a Netgear wireless router modem that connects wirelessly to my printer. Works a treat in windows

In System settings/printing/add/network printer...now you have about 7 options and I have no idea which one to use or what address to type in

---

### Post by Kaizoku001 on 2012-05-17
> **losbey said:**
> a lot of help here but what I need it set it up as a network printer, printer is a MG650

My setup is a Netgear wireless router modem that connects wirelessly to my printer. Works a treat in windows

In System settings/printing/add/network printer...now you have about 7 options and I have no idea which one to use or what address to type in

Ilthere's an option in the system>printer>setting.
No to sure where thought. I'll check it out tonight when I get home.
It helps enabling share printing. 
Mine worke great now.

---

### Post by loseby on 2012-05-18
well some sort of success by finding out the network address from the router ...address is 10.1.1.7 and added that to the add netwrok printer and app socket and putting 10.1.1.7  and following it from there

Have managed to get the MG6150 to print but the colours are way out and it wont use the paper cartridge   ...you need to load paper from the back

---

### Post by Houmie on 2012-05-24
Thank everyone for the fantastic help here.

I can confirm that the most recent Canon drivers work well on Ubuntu 12.04 64bit.  Simply run the install script as sudo.

However one problem I have is how do you save the scanned documents in PDF?  I tried print to file and selected PDF, but its 7 mb big.  Unacceptable.  According to teh guide I should be able to save as and select PDF as extension. BUt I see only image extensions. I see no where PDF.

Another problem is how do you multi-page scan several documents into one PDF?

This is the only task that I have to dual boot into Windows. Very annoying. Everything else has been replaced by Ubuntu.

Any help would be appreciated,

---

### Post by Houmie on 2012-06-18
> **Kaizoku001 said:**
> 
But I still can get xsane to work, GIMP is good for scaning 1 file, but sometimes I have to scan a whole book. Saving one file at a time is hell.

Hi Kaizoku001,

I have the exact same problem, have you found the solution for this?

Many Thanks,
Houman

---

