---
title: "Brother Scanner on Ubuntu Server - how to convert raw scans?"
date: 2009-10-25
forum: Server Platforms
---

### Post by rrohde on 2009-10-25
Hi everyone, 

I thought it would be nice to use my Ubuntu server (9.04) to share a printer/scanner (Brother DCP 150C). The installation of the needed files was easy enough, and the printer works with CUPS, the scanner works with the Brother software (brscan2 and brscan-skey). 

Currently, document scanned ends up as a Netpbm PPM "rawbits" image data in /root/brscan.

There are 2 problems with that scenario: 

1) Scanned files end up under root, and thus are not easy to share to other users on the network.

2) The rawbits file cannot be used by other users in that format.  


Questions: 

- How can I configure the brscan-skeys tool to scan as a non-root user? 

- How can I make it so that a scan is either converted as PDF or JPG (or any other usable image format) on the fly? 

The Ubuntu server does not run X Windows, so it's a pure commandline environment. I have sane-utils installed (as mentioned on Brother's website). 

Any help is greatly appreciated. 

Cheers, 
Rainer

---

### Post by lionel47 on 2009-10-31
I am trying to do the same thing except I am using Xubuntu as the server OS.  Any help is greatly appreciated.  I think you should be able to share a scanner over the network.

---

### Post by rrohde on 2009-10-31
Well, here's an update: 

I was able to change the scantofile-0.2.1-3.sh script in /usr/local/Brother/sane/script/scantofile-0.2.1-3.sh a bit to do what I require: 

- I changed the resolution to 300

- Then I added a few commands to be able to a) convert the raw image file to tiff and b) then copy the scanned file to a shared directory which everyone can access from the network equally well:  

scanimage --format=tiff --device-name "$device" --resolution $resolution> $output_file.tiff && cp $output_file.tiff /STORAGE1/SCANNED/ && chown -R scanner.users /STORAGE1/SCANNED/*.tiff && rm -fr /root/brscan/*

This works for me now. Not pretty, not perfect, but it works. :)

---

