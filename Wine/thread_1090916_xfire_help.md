---
title: "xfire help"
date: 2009-03-08
forum: Wine
---

### Post by mikedmor on 2009-03-08
I just installed xfire using wine and now anytime i click any part of xfire (except the area to move it) it freezes. i found a guide that explained how to fix the fonts and followed it but that about it. once i click on any area i get the crash report. here is the procedure i followed to fix the fonts:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh winetricks allfonts
sh winetricks ie6
sh winetricks comctl32
sh winetricks comctl32.ocx

And i will post the crash report here too just incase it can help at all:

```
<?xml version="1.0" encoding="utf-8" ?>

<ExceptionReport Version="4">
	<Application Build="35995" Command="&quot;C:\Program Files\Xfire\Xfire.exe&quot;"/>
	<OperatingSystem Type="2"><Version Major="5" Minor="1" Build="2600"/></OperatingSystem>
	<Exception Code="C0000005" Address="031AB08F"><Module Section="0003" Offset="0017208F" FileName="C:\Program Files\Xfire\xfire_toucan_35995.dll"/></Exception>
	<Registers EAX="031B2F5C" EBX="7ECEFFF4" ECX="7ED0FDC0" EDX="0000002F" ESI="00000000" EDI="50010000" CS="0073" EIP="031AB08F" SS="007B" ESP="0032F424" EBP="0032F42C" DS="007B" ES="007B" FS="0033" GS="003B" Flags="00210292"/>
	<BackTrace>
		<Frame ProgramCounter="031AB08F" StackAddress="0032F424" FrameAddress="0032F42C">
			<Module Section="0003" Offset="0017208F" FileName="C:\Program Files\Xfire\xfire_toucan_35995.dll"/>
			<StackHexDump From="0032F424" To="0032F42C">65 2f 1b 03	f4 ff ce 7e</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7EC37270" StackAddress="0032F434" FrameAddress="0032F4FC">
			<Module Section="0001" Offset="00016270" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F42C" To="0032F4AC">fc f4 32 00	70 72 c3 7e	a0 00 02 00	f0 ff ff ff	4c f4 32 00	60 9e cb 7e	c0 fd d0 7e	07 00 00 00	2f 00 00 00	a0 00 02 00	a0 00 02 00	a0 00 02 00	6c f4 32 00	30 9e cb 7e	c0 fd d0 7e	f4 ff ce 7e	00 00 00 00	c5 df cb 7e	a0 00 02 00	00 10 00 00	44 80 fd 7f	00 01 00 00	18 00 00 00	a0 00 02 00	01 00 00 00	01 02 00 00	a0 00 02 00	00 00 00 00	00 00 00 00	8c 94 ce 7c	00 00 00 00	c8 94 ce 7c</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7EC3861A" StackAddress="0032F504" FrameAddress="0032F51C">
			<Module Section="0001" Offset="0001761A" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F4FC" To="0032F51C">1c f5 32 00	1a 86 c3 7e	01 00 00 00	2f 00 07 00	01 00 00 00	2f 1a 89 7b	f4 ff ce 7e	01 02 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7ECC96AA" StackAddress="0032F524" FrameAddress="0032F54C">
			<Module Section="0001" Offset="000A86AA" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F51C" To="0032F54C">4c f5 32 00	aa 96 cc 7e	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	e8 4f 05 00	f4 ff ce 7e	4c f5 32 00	f4 ff ce 7e	01 02 00 00	a0 00 02 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7ECC9AFA" StackAddress="0032F554" FrameAddress="0032F58C">
			<Module Section="0001" Offset="000A8AFA" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F54C" To="0032F58C">8c f5 32 00	fa 9a cc 7e	d0 85 c3 7e	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	00 00 00 00	f4 8f 39 7e	28 8f ce 7c	ea ee ff ff	cd 8f ff ff	e5 f0 2e 7e	f4 ff ce 7e	d0 85 c3 7e	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7ECCDA62" StackAddress="0032F594" FrameAddress="0032F5CC">
			<Module Section="0001" Offset="000ACA62" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F58C" To="0032F5CC">cc f5 32 00	62 da cc 7e	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	c4 f5 32 00	d0 85 c3 7e	30 f6 32 00	00 00 00 00	1c 3d 49 01	00 b5 16 00	dc f5 32 00	2d d4 4d 00	d8 f5 32 00	01 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004DDA44" StackAddress="0032F5D4" FrameAddress="0032F6C4">
			<Module Section="0001" Offset="000DCA44" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="0032F5CC" To="0032F64C">c4 f6 32 00	44 da 4d 00	d0 85 c3 7e	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	a0 00 02 00	01 02 00 00	f4 ff ce 7e	1c f7 32 00	40 00 00 00	53 02 00 00	00 00 00 00	48 f6 32 00	40 00 00 00	40 f7 32 00	48 f6 32 00	04 21 ec b7	1a 92 ca 7e	31 bb c6 7b	05 00 00 00	40 f7 32 00	40 00 00 00	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	f4 4f c9 7b	00 00 00 00	80 f7 32 00	01 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7ECC96AA" StackAddress="0032F6CC" FrameAddress="0032F6F4">
			<Module Section="0001" Offset="000A86AA" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F6C4" To="0032F6F4">f4 f6 32 00	aa 96 cc 7e	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	2c f7 32 00	f4 ff ce 7e	f4 f6 32 00	f4 ff ce 7e	01 02 00 00	a0 00 02 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7ECC9AFA" StackAddress="0032F6FC" FrameAddress="0032F734">
			<Module Section="0001" Offset="000A8AFA" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F6F4" To="0032F734">34 f7 32 00	fa 9a cc 7e	c6 d6 4d 00	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	f4 ff ce 7e	34 f7 32 00	f4 ff ce 7e	00 80 fd 7f	a0 00 02 00	34 f7 32 00	f4 ff ce 7e	44 80 fd 7f	a0 00 02 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7ECCEE27" StackAddress="0032F73C" FrameAddress="0032F774">
			<Module Section="0001" Offset="000ADE27" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F734" To="0032F774">74 f7 32 00	27 ee cc 7e	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	a4 f7 32 00	c6 d6 4d 00	f4 7f 8b 7b	d0 0f 14 00	6c f7 32 00	0b f6 41 00	14 1c d3 7e	f4 ff ce 7e	40 f8 32 00	20 f8 32 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7EC8E1B6" StackAddress="0032F77C" FrameAddress="0032F7B4">
			<Module Section="0001" Offset="0006D1B6" FileName="C:\windows\system32\user32.dll"/>
			<StackHexDump From="0032F774" To="0032F7B4">b4 f7 32 00	b6 e1 c8 7e	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	a4 f7 32 00	01 00 00 00	04 00 00 00	2d d4 4d 00	b0 f7 32 00	00 b5 16 00	40 f8 32 00	d0 0f 14 00	40 f8 32 00	34 02 66 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004C6F0D" StackAddress="0032F7BC" FrameAddress="0032F9B8">
			<Module Section="0001" Offset="000C5F0D" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="0032F7B4" To="0032F834">b8 f9 32 00	0d 6f 4c 00	20 f8 32 00	01 00 00 00	00 00 00 00	00 00 74 7d	74 00 20 00	54 00 69 00	6d 00 65 00	00 00 00 00	00 00 03 00	00 00 02 00	02 00 00 00	00 00 00 00	c4 ff ff ff	20 d8 78 c1	52 a0 c9 01	f4 9f b6 7e	00 00 00 00	00 75 12 00	34 f8 32 00	75 96 b5 7e	20 f8 32 00	40 f8 32 00	75 96 b5 7e	2c f8 32 00	d7 97 42 00	a0 00 02 00	01 02 00 00	01 00 00 00	2f 00 07 00	c0 0e 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004A6BED" StackAddress="0032F9C0" FrameAddress="0032FEA4">
			<Module Section="0001" Offset="000A5BED" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="0032F9B8" To="0032FA38">a4 fe 32 00	ed 6b 4a 00	a0 0d 14 00	00 00 00 00	f4 7f 8b 7b	08 00 00 00	ff 00 00 00	01 00 00 00	10 00 00 00	00 00 00 00	d0 0f 14 00	a0 0d 14 00	f4 4f c9 7b	70 aa 15 00	f8 8b fd 7f	24 fa 32 00	26 4b c6 7b	0c 00 00 00	0f 00 00 00	32 00 00 00	00 00 00 c0	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	07 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="004D5316" StackAddress="0032FEAC" FrameAddress="0032FF08">
			<Module Section="0001" Offset="000D4316" FileName="C:\Program Files\Xfire\Xfire.exe"/>
			<StackHexDump From="0032FEA4" To="0032FF08">08 ff 32 00	16 53 4d 00	00 00 40 00	00 00 00 00	a0 0d 14 00	0a 00 00 00	be 52 4d 00	00 f0 fd 7f	44 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	01 00 00 00	00 00 00 00	04 00 00 00	08 00 00 00	0c 00 00 00</StackHexDump>
		</Frame>
		<Frame ProgramCounter="7B878700" StackAddress="0032FF10" FrameAddress="0032FFE8">
			<Module Section="0001" Offset="00057700" FileName="C:\windows\system32\KERNEL32.dll"/>
			<StackHexDump From="0032FF08" To="0032FF88">e8 ff 32 00	00 87 87 7b	00 f0 fd 7f	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	ff ff ff ff	60 87 87 7b	30 5a 84 7b	f4 7f 8b 7b	01 00 00 00	18 00 00 00	e8 ff 32 00	41 ca b1 5f	b6 c0 43 35	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00	00 00 00 00</StackHexDump>
		</Frame>
	</BackTrace>
</ExceptionReport>
```

Thanks

-Mike

---

### Post by Poyntz on 2009-06-08
Hey Mike,

That's a windows crash report, so unfortunately no good here :/.

Anyhow, I've been having the crash problem as well. 
Try my tutorial here: [http://ubuntuforums.org/showthread.php?t=1181645&highlight=xfire](http://ubuntuforums.org/showthread.php?t=1181645&highlight=xfire)

Hopefully it works for you too :)

---

