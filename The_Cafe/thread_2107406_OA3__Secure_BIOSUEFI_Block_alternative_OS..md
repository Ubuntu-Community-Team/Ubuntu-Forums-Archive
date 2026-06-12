---
title: "OA3 / Secure BIOS/UEFI: Block alternative OS."
date: 2013-01-21
forum: The Cafe
---

### Post by exMCSE2000 on 2013-01-21
Has anyone else run in to issues with Hardware manufactures implementing OA3 support?
   
  When Intel updated the BIOS for the BZ68DC system board (v035) they implemented OA3 and to comply with MS requirements they block you from downgrading.  No BIOS for this board will work with any OS other then OA2.2/3.0 OS like 2012 (and theres no drivers for 2012) and Windows 8.  Per Intel forums Windows 7 is also now unsupported on the DZ68BC. 

   
  Some boards like MSI, ASUS and Intel are now shipping with firmware that can not be downgraded and block the install of any OS other then MS server 2012 and Windows 8. (Example: Intel DZ77GAL-70K).  
   
  HP now has OA3 BIOS on systems that didn&#8217;t even ship with 7 let alone 8.  The recent XW6600 and XW8600 BIOS 1.45 has the OA3 module that blocks downgrading, this BIOS disable two of the back USBs on MS OS and all the USB on other OS.  So allot of people were systemless (unless they had a backup ps2 kb) until HP released 1.46.  Thank fully HP didn&#8217;t include the MS secure BS.  (Otherwise all 3 of my computers would be unusable).
   
  All the above problems are to comply with the OEM contracts of MS of protecting OA ROM space independent of your OS or if the product was sold as OS free only.
   
  I&#8217;m thinking the only option to get our fair use rights of our HARDWARE back is a class action against MS over OA3. 
   
  Community thoughts?

---

### Post by sidzen on 2013-01-21
Go for it!  Better have some bucks!

---

### Post by exMCSE2000 on 2013-01-21
Bucks aren&#8217;t the issue.
 
It&#8217;s is there enough for a class to hurt Microsoft and force them to change the lock out for those of us that are not MS users (at least at home). 
 
I work for a multi-platform IT solution provider, the fact I&#8217;m force to use Microsoft Corporate products at work, would that tie me the EULA personally even though I&#8217;m a custom DUETEFI/BSD user at home? 
 
The problem is finding the class (that is not tied to the EULA) big enough for a lawyer to take. If your tied to the EULA the ATT decision basically says arbitration only (with or without a class) and the lack of jury will guaranty a decision in favor of Balmer.

---

### Post by grahammechanical on 2013-01-22
If, like me, you have no idea what this thread is about, then this might help:

[http://www.mydigitallife.info/windows-8-to-have-oem-activation-3-0/]("http://www.mydigitallife.info/windows-8-to-have-oem-activation-3-0/")

As they say, the devil is in the detail. I still do not have any detail as to why this will stop Linux from being installed on a machine with a BIOS/UEFI that has OEM Action 3 with or without Windows 8 installed.

We already have people buying Windows 8 machines (presumably with OA3 in the BIOS). Many are posting on this forum of their attempts to install Ubuntu (Do not try anything but 12.10). Some are succeeding without problems. Some are suceeding with difficulty.

I see issues arising from an expectation of a plug and play installation of Ubuntu. No. Do the research. And a varied implementation by OEMs of the UEFI and Secure Boot specification.

Is OA3 effecting attempts to install Ubuntu on these machines?

Regards.

---

