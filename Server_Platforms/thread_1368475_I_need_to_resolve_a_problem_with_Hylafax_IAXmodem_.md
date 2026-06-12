---
title: "I need to resolve a problem with Hylafax IAXmodem and Gfax"
date: 2009-12-30
forum: Server Platforms
---

### Post by richardsith on 2009-12-30
Hello,
it's the first time I write here, and I'm sorry for my English. I hope that there is someone that can help me to resolve a problem with that applications. The situation is the following, I've configured a FoIP Server using Ubuntu 8.04Lts Server with installed Asterisk, Hylafax, IAXModem and GFax on its client Desktop (Ubuntu 9.10 Desktop Edition). The problem is, when try to send a file (example issue.net) from GFax, the application signs me a fail without give me a log. While on the Server is presented a log that reports the following report, and the file doesn't arrive to destination

Jan 01 22:23:11.16: [ 6703]: SESSION BEGIN 000000029 390863707331875163
Jan 01 22:23:11.16: [ 6703]: HylaFAX (tm) Version 4.4.3
Jan 01 22:23:11.16: [ 6703]: SEND FAX: JOB 41 DEST 707331875163 COMMID 000000029 DEVICE '/dev/ttyIAX0' FROM 'ric ' USER ric
Jan 01 22:23:11.16: [ 6703]: <-- [12:AT+FCLASS=1\r]
Jan 01 22:23:11.16: [ 6703]: --> [2:OK]
Jan 01 22:23:11.16: [ 6703]: DIAL 707331875163
Jan 01 22:23:11.16: [ 6703]: <-- [17:ATDT707331875163\r]
Jan 01 22:23:19.55: [ 6703]: --> [7:CONNECT]
Jan 01 22:23:21.05: [ 6703]: --> [2:OK]
Jan 01 22:23:21.05: [ 6703]: REMOTE NSF "AD 00 55 48 79 6C 61 46 41 58 20 28 74 6D 29 20 56 65 72 73 69 6F 6E 20 36 2E 30 2E 33"
Jan 01 22:23:21.05: [ 6703]: NSF remote fax equipment: HylaFAX
Jan 01 22:23:21.05: [ 6703]: NSF remote station ID: "HylaFAX (tm) Version 6.0.3"
Jan 01 22:23:21.05: [ 6703]: <-- [9:AT+FRH=3\r]
Jan 01 22:23:21.76: [ 6703]: --> [7:CONNECT]
Jan 01 22:23:21.76: [ 6703]: --> [2:OK]
Jan 01 22:23:21.76: [ 6703]: REMOTE CSI "VozToVoice"
Jan 01 22:23:21.76: [ 6703]: <-- [9:AT+FRH=3\r]
Jan 01 22:23:22.22: [ 6703]: --> [7:CONNECT]
Jan 01 22:23:22.32: [ 6703]: --> [2:OK]
Jan 01 22:23:22.32: [ 6703]: REMOTE best rate 14400 bit/s
Jan 01 22:23:22.32: [ 6703]: REMOTE max A3 page width (303 mm)
Jan 01 22:23:22.32: [ 6703]: REMOTE max unlimited page length
Jan 01 22:23:22.32: [ 6703]: REMOTE best vres R16 x 15.4 line/mm
Jan 01 22:23:22.32: [ 6703]: REMOTE format support: MH, MR, MMR
Jan 01 22:23:22.32: [ 6703]: REMOTE supports T.30 Annex A, 256-byte ECM
Jan 01 22:23:22.32: [ 6703]: REMOTE best 0 ms/scanline
Jan 01 22:23:22.32: [ 6703]: USE 14400 bit/s
Jan 01 22:23:22.32: [ 6703]: USE error correction mode
Jan 01 22:23:22.32: [ 6703]: <-- [9:AT+FRS=7\r]
Jan 01 22:23:22.36: [ 6703]: --> [2:OK]
Jan 01 22:23:22.36: [ 6703]: <-- [9:AT+FTH=3\r]
Jan 01 22:23:22.38: [ 6703]: --> [7:CONNECT]
Jan 01 22:23:22.38: [ 6703]: <-- data [3]
Jan 01 22:23:22.38: [ 6703]: <-- data [2]
Jan 01 22:23:23.45: [ 6703]: --> [2:OK]
Jan 01 22:23:24.45: [ 6703]: <-- [5:ATH0\r]
Jan 01 22:23:24.55: [ 6703]: --> [2:OK]
Jan 01 22:23:24.55: [ 6703]: SESSION END


At first check I don't see any error but my receiver don't receive that. While, if make the same step but using the command "sendfax -n -d xxxxxxxxxxx /etc/issue.net " from the Server, the fax goes to destination. 
The second one is its own log

Jan 01 22:20:10.38: [ 6272]: SESSION BEGIN 000000028 390863707331875163
Jan 01 22:20:10.38: [ 6272]: HylaFAX (tm) Version 4.4.3
Jan 01 22:20:10.38: [ 6272]: SEND FAX: JOB 40 DEST 707331875163 COMMID 000000028 DEVICE '/dev/ttyIAX0' FROM 'ric ' USER ric
Jan 01 22:20:10.38: [ 6272]: <-- [12:AT+FCLASS=1\r]
Jan 01 22:20:10.38: [ 6272]: --> [2:OK]
Jan 01 22:20:10.38: [ 6272]: DIAL 707331875163
Jan 01 22:20:10.38: [ 6272]: <-- [17:ATDT707331875163\r]
Jan 01 22:20:19.03: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:20.39: [ 6272]: --> [2:OK]
Jan 01 22:20:20.39: [ 6272]: REMOTE NSF "AD 00 55 48 79 6C 61 46 41 58 20 28 74 6D 29 20 56 65 72 73 69 6F 6E 20 36 2E 30 2E 33"
Jan 01 22:20:20.39: [ 6272]: NSF remote fax equipment: HylaFAX
Jan 01 22:20:20.39: [ 6272]: NSF remote station ID: "HylaFAX (tm) Version 6.0.3"
Jan 01 22:20:20.39: [ 6272]: <-- [9:AT+FRH=3\r]
Jan 01 22:20:21.07: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:21.07: [ 6272]: --> [2:OK]
Jan 01 22:20:21.07: [ 6272]: REMOTE CSI "VozToVoice"
Jan 01 22:20:21.07: [ 6272]: <-- [9:AT+FRH=3\r]
Jan 01 22:20:21.48: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:21.53: [ 6272]: --> [2:OK]
Jan 01 22:20:21.53: [ 6272]: REMOTE best rate 14400 bit/s
Jan 01 22:20:21.53: [ 6272]: REMOTE max A3 page width (303 mm)
Jan 01 22:20:21.53: [ 6272]: REMOTE max unlimited page length
Jan 01 22:20:21.53: [ 6272]: REMOTE best vres R16 x 15.4 line/mm
Jan 01 22:20:21.53: [ 6272]: REMOTE format support: MH, MR, MMR
Jan 01 22:20:21.53: [ 6272]: REMOTE supports T.30 Annex A, 256-byte ECM
Jan 01 22:20:21.53: [ 6272]: REMOTE best 0 ms/scanline
Jan 01 22:20:21.53: [ 6272]: USE 14400 bit/s
Jan 01 22:20:21.53: [ 6272]: USE error correction mode
Jan 01 22:20:21.53: [ 6272]: SEND file "docq/doc39.ps;f0"
Jan 01 22:20:21.53: [ 6272]: USE A4 page width (215 mm)
Jan 01 22:20:21.53: [ 6272]: USE unlimited page length
Jan 01 22:20:21.53: [ 6272]: USE 3.85 line/mm
Jan 01 22:20:21.53: [ 6272]: USE 2-D MMR
Jan 01 22:20:21.53: [ 6272]: USE 0 ms/scanline
Jan 01 22:20:21.53: [ 6272]: SEND training at v.17 14400 bit/s
Jan 01 22:20:21.53: [ 6272]: <-- [9:AT+FRS=7\r]
Jan 01 22:20:21.59: [ 6272]: --> [2:OK]
Jan 01 22:20:21.59: [ 6272]: <-- [9:AT+FTH=3\r]
Jan 01 22:20:21.60: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:21.60: [ 6272]: <-- data [23]
Jan 01 22:20:21.60: [ 6272]: <-- data [2]
Jan 01 22:20:23.13: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:23.13: [ 6272]: <-- data [7]
Jan 01 22:20:23.13: [ 6272]: <-- data [2]
Jan 01 22:20:23.53: [ 6272]: --> [2:OK]
Jan 01 22:20:23.53: [ 6272]: <-- [9:AT+FTS=7\r]
Jan 01 22:20:23.61: [ 6272]: --> [2:OK]
Jan 01 22:20:23.61: [ 6272]: <-- [11:AT+FTM=145\r]
Jan 01 22:20:23.62: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:23.62: [ 6272]: DELAY 400 ms
Jan 01 22:20:24.01: [ 6272]: <-- data [1024]
Jan 01 22:20:24.01: [ 6272]: <-- data [1024]
Jan 01 22:20:24.01: [ 6272]: <-- data [652]
Jan 01 22:20:24.01: [ 6272]: <-- data [2]
Jan 01 22:20:26.57: [ 6272]: --> [2:OK]
Jan 01 22:20:26.57: [ 6272]: <-- [9:AT+FRH=3\r]
Jan 01 22:20:27.05: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:27.98: [ 6272]: --> [2:OK]
Jan 01 22:20:27.98: [ 6272]: TRAINING succeeded
Jan 01 22:20:27.98: [ 6272]: SEND begin page
Jan 01 22:20:27.98: [ 6272]: SEND EOFB
Jan 01 22:20:27.98: [ 6272]: SEND send frame number 0
Jan 01 22:20:27.98: [ 6272]: SEND send frame number 1
Jan 01 22:20:27.98: [ 6272]: SEND send frame number 2
Jan 01 22:20:27.98: [ 6272]: <-- [9:AT+FRS=7\r]
Jan 01 22:20:28.02: [ 6272]: --> [2:OK]
Jan 01 22:20:28.02: [ 6272]: <-- [11:AT+FTM=146\r]
Jan 01 22:20:28.04: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:28.04: [ 6272]: DELAY 400 ms
Jan 01 22:20:28.43: [ 6272]: <-- data [1028]
Jan 01 22:20:28.43: [ 6272]: <-- data [161]
Jan 01 22:20:28.43: [ 6272]: <-- data [2]
Jan 01 22:20:29.15: [ 6272]: --> [2:OK]
Jan 01 22:20:29.15: [ 6272]: <-- [9:AT+FTS=9\r]
Jan 01 22:20:29.25: [ 6272]: --> [2:OK]
Jan 01 22:20:29.25: [ 6272]: <-- [9:AT+FTH=3\r]
Jan 01 22:20:29.26: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:29.26: [ 6272]: <-- data [7]
Jan 01 22:20:29.26: [ 6272]: <-- data [2]
Jan 01 22:20:30.43: [ 6272]: --> [2:OK]
Jan 01 22:20:30.43: [ 6272]: SEND send PPS (partial page signal)
Jan 01 22:20:30.43: [ 6272]: SEND send EOP (no more pages or documents)
Jan 01 22:20:30.44: [ 6272]: <-- [9:AT+FRH=3\r]
Jan 01 22:20:30.94: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:31.80: [ 6272]: --> [2:OK]
Jan 01 22:20:31.80: [ 6272]: SEND recv MCF (message confirmation)
Jan 01 22:20:31.80: [ 6272]: <-- [9:AT+FRS=7\r]
Jan 01 22:20:31.84: [ 6272]: --> [2:OK]
Jan 01 22:20:31.84: [ 6272]: SEND end page
Jan 01 22:20:31.86: [ 6272]: SEND FAX (000000028): FROM ric@ubuntu TO 707331875163 (page 1 of 1 sent in 0:10)
Jan 01 22:20:31.86: [ 6272]: SEND FAX (000000028): FROM ric@ubuntu TO 707331875163 (docq/doc39.ps;f0 sent in 0:10)
Jan 01 22:20:32.87: [ 6272]: <-- [9:AT+FTH=3\r]
Jan 01 22:20:32.87: [ 6272]: --> [7:CONNECT]
Jan 01 22:20:32.87: [ 6272]: <-- data [3]
Jan 01 22:20:32.87: [ 6272]: <-- data [2]
Jan 01 22:20:33.93: [ 6272]: --> [2:OK]
Jan 01 22:20:34.94: [ 6272]: <-- [5:ATH0\r]
Jan 01 22:20:35.03: [ 6272]: --> [2:OK]
Jan 01 22:20:35.03: [ 6272]: SESSION END

Why?????
Please help me!!! 
Ah, I've also added an user to use it from the remote pc and inserted the IP  address on file hosts.hfaxd.

Thanks a lot in advance

---

### Post by richardsith on 2010-01-02
Hello guys,
I've checked the directories doneq, docq 'n tmp on /var/spool/hylafax and I saw some files with the extention type docx.ps and decx.ps.x in docq.
For that files sent from server its own format is docx.ps and report something like these lines

%!PS-Adobe-3.0
%%Creator: HylaFAX TextFormat Class
%%Title:
%%CreationDate: Fri Jan 1 22:19:57 2010
%%For:
%%Origin: 0 0
%%BoundingBox: 0 0 612 792
%%Pages: (atend)
%%PageOrder: Ascend
%%Orientation: Portrait
%%DocumentNeededResources: font Courier-Bold
%%EndComments
%%BeginProlog
/$printdict 50 dict def $printdict begin
/ISOLatin1Encoding where{pop save true}{false}ifelse
/ISOLatin1Encoding[
/.notdef /.notdef /.notdef /.notdef /.notdef /.notdef
/.notdef /.notdef /.notdef /.notdef /.notdef /.notdef
/.notdef /.notdef /.notdef /.notdef /.notdef /.notdef
/.notdef /.notdef /.notdef /.notdef /.notdef /.notdef
/.notdef /.notdef /.notdef /.notdef /.notdef /.notdef
/.notdef /.notdef /space /exclam /quotedbl /numbersign
/dollar /percent /ampersand /quoteright /parenleft
/parenright /asterisk /plus /comma /minus /period
/slash /zero /one /two /three /four /five /six /seven
/eight /nine /colon /semicolon /less /equal /greater
/question /at /A /B /C /D /E /F /G /H /I /J /K /L /M
/N /O /P /Q /R /S /T /U /V /W /X /Y /Z /bracketleft
/backslash /bracketright /asciicircum /underscore
/quoteleft /a /b /c /d /e /f /g /h /i /j /k /l /m
/n /o /p /q /r /s /t /u /v /w /x /y /z /braceleft
/bar /braceright /asciitilde /guilsinglright /fraction
/florin /quotesingle /quotedblleft /guilsinglleft /fi
/fl /endash /dagger /daggerdbl /bullet /quotesinglbase
/quotedblbase /quotedblright /ellipsis /trademark
/perthousand /grave /scaron /circumflex /Scaron /tilde
/breve /zcaron /dotaccent /dotlessi /Zcaron /ring
/hungarumlaut /ogonek /caron /emdash /space /exclamdown
/cent /sterling /currency /yen /brokenbar /section
/dieresis /copyright /ordfeminine /guillemotleft
/logicalnot /hyphen /registered /macron /degree
/plusminus /twosuperior /threesuperior /acute /mu
...........
...........

while for the files sent by Gfax Client the extention is docx.ps.x and these last ones don't arrived to destination.

---

