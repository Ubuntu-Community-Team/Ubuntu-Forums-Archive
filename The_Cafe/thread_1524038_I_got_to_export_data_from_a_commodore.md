---
title: "I got to export data from a commodore"
date: 2010-07-04
forum: The Cafe
---

### Post by themarker0 on 2010-07-04
Any idea how? Its a crapload of data. I don't mind doing the work, but i can't type it out.

---

### Post by McRat on 2010-07-04
> **themarker0 said:**
> Any idea how? Its a crapload of data. I don't mind doing the work, but i can't type it out.

ASCII data?

Do you have a printer?

If so, get a cheap Parallel to RS-232 or USB converter, then open up a "terminal" program on the target system.  Not sure which Linux program is a terminal program (No Not The CLI, a Terminal program is a program that reads an ASCII stream from a modem or COMport, this name predates Linux).

Sometimes you must write your own if the stream can't be read by the terminal program correctly.  They aren't hard in BASIC, about 5 lines of code.

---

### Post by Bachstelze on 2010-07-04
> **McRat said:**
> 
If so, get a cheap Parallel to RS-232 or USB converter, then open up a "terminal" program on the target system.  Not sure which Linux program is a terminal program (No Not The CLI, a Terminal program is a program that reads an ASCII stream from a modem or COMport, this name predates Linux).

minicom, screen, cu. Among others.

---

### Post by jflaker on 2010-07-04
> **themarker0 said:**
> Any idea how? Its a crapload of data. I don't mind doing the work, but i can't type it out.

BBS?

Upload the file as a text file (flat file) to a dial up BBS, which you can still find believe it or not.....Then download from that bbs to your computer to be parsed later.  The transfer protocols will take care of the data conversion if needed as the data moves from your computer to another system and back.

The files can't be that big as the storage was limited on the commodore.....

A few of these BBS's still have dial and also are accessible via the internet.....

Also, this MAY be of interest.....
[http://www.root.org/~nate/c64/x1541.html]("http://www.root.org/~nate/c64/x1541.html")

---

### Post by earthpigg on 2010-07-04
what a fun project.

I love history, and it's important to keep needed data alive as time progresses. it only gets more difficult with time.

good thing that your orginization is having you do this now, else it may find itself in the same shoes as the Governator, unable to change how much money gets paid to employees.

---

### Post by themarker0 on 2010-07-04
> **earthpigg said:**
> what a fun project.

I love history, and it's important to keep needed data alive as time progresses. it only gets more difficult with time.

good thing that your orginization is having you do this now, else it may find itself in the same shoes as the Governator, unable to change how much money gets paid to employees.

This is just a friends stuff not a companies. If my work had its data on a C64... I'd crapmyself, i already have 1tb of data to make paperless, don't need more :(

---

### Post by gordintoronto on 2010-07-04
You might try asking on the forums at TPUG. (Toronto PET Users Group, which has been around for 30 years.) [www.tpug.ca](www.tpug.ca)

---

### Post by Dr. C on 2010-07-04
Here is an option. [http://www.kotinet.com/1541/]("http://www.kotinet.com/1541/") This allows a PC running DOS to emulate the Commodore floppy drive over the PC parallel port. It also shows how to make the adapter cable and one can purchase the cable parts from [here]("http://ist.uwaterloo.ca/~schepers/cables.html")

---

### Post by SoFl W on 2010-07-04
Can you still buy a null modem at some place like radio shack?  Or just get a cross-over cable?

---

### Post by Dr. C on 2010-07-05
> **SoFl W said:**
> Can you still buy a null modem at some place like radio shack?  Or just get a cross-over cable?

I do not believe the Commodore has a RS 232 serial port. If it did then a null modem cable would be an option. As for Ethernet I really do not think so. 

I thought floppies. This can work if the Commodore supports any of 360K 5.25in, 1.2M 5.25in, 720K 3.5in, or 1.44M 3.5in; however I am not sure if it does.

---

### Post by lisati on 2010-07-05
The project sounds interesting. It reminds me something I was thinking of doing a few years ago, namely to figure out how to get the 5.25" disk drives on a Commodore 128 reading disks produced on an MS-DOS machine. The minimal research I did at the time suggested that it could be done but I didn't have the patience to learn enough to get it figured out.

Good luck!

---

### Post by McRat on 2010-07-05
IIRC, when you call the BIOS disk functions, you define the # of tracks and sectors, then seek accordingly.  I'm pretty sure a BIOS read will take in garbage, as long as there is a sector marker.  Obviously you can't use the DOS (or Win, or Linux) read functions directly as they are based on directory listings.  

If the Commodore disks are hard sectored (there is a small hole for the sector mark, a DOS disk or Apple disk will only have 1, a hard sector disk will have like 11, 13, 15? or so), then it's a no-go.

It's worth a shot if you understand about how disk reads are done at the interrupt level, if you don't, it would be a serious challenge.  You can use any language or operating system that supports 5.25" floppies and calling BIOS interrupts directly.  I'd use DOS as it's fairly simple as far as "simple" goes.  MS Professional Basic will permit BIOS calls directly, I'd use that.  

Heck, you MIGHT even be able to do it manually through DEBUG,  IIRC, there is a function that permits BIOS disk reads by sector and track.

Even if you could read the sectors, you'd have to do a lot of work to reconstruct it without a directory map for the Commodore.

Like someone else said, I don't remember the Commodore having a COM post, but I thought it had a PRN port.  I've used the PRN->RS232 method on several incompatible computers, and I still use it today with my CP/M machines.  It will work, and it's not hard.  You don't have to write any code, and the files come out fully intact.  Binaries will be lost, but WTF would you need a Commodore binary for but a Commodore.

---

### Post by SoFl W on 2010-07-05
> **FineE said:**
> I do not believe the Commodore has a RS 232 serial port. If it did then a null modem cable would be an option. As for Ethernet I really do not think so. 

You maybe right.  I didn't have one, how was the modem hooked up?  Was it a cartridge?  ( I think it is coming back to me)
According to wikipedia the ports on the C64 are: 2× CIA 6526 Joystick,  Power,  Cartridge, RF,  A/V,  IEEE-488  Floppy/Printer, Digital tape,  GPIO/RS-232
I was thinking that we had a serial cross over cable for something at work but I don't remember what it was. It was no longer in use but we had the cable in our tangled "box of tangled cables"[COLOR=LightBlue]*****[/COLOR]   But it doesn't matter if the C64 didn't have a serial port.

> **FineE said:**
>  I thought floppies. This can work if the Commodore supports any of 360K 5.25in, 1.2M 5.25in, 720K 3.5in, or 1.44M 3.5in; however I am not sure if it does.

I think somehow using an old dial up BBS configuration might be best.  It only has to work from the C64 to the dialup.  If the dial up has a floppy or usb port you than have modern, easier access to the data.

[COLOR=Gray][COLOR=LightBlue]*****[/COLOR]Not sure about that box, you could put a cable on top, come back the next day and it would someone be tangled in with the rest of the cables.  I think the Christmas tree light gnomes might come in and tangle all cables.[/COLOR]

---

### Post by SoFl W on 2010-07-05
I googled something but didn't watch [these videos]("http://www.google.com/search?q=transfer+commodore+64+data+to+a+pc&hl=en&prmd=v&source=univ&tbs=vid:1&tbo=u&ei=AcsxTKCZIMH98AaglNzICw&sa=X&oi=video_result_group&ct=title&resnum=4&ved=0CCoQqwQwAw") to know if they would work.

---

