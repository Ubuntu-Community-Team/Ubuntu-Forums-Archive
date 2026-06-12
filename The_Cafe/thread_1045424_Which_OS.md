---
title: "Which OS?"
date: 2009-01-20
forum: The Cafe
---

### Post by daniel014 on 2009-01-20
I completely love Ubuntu but hate Windows.

Ubuntu is absolutely fine except I want to be able to use MS Office, but without dual booting.

Any help? Thanks in advance.

---

### Post by glotz on 2009-01-20
Why MS Office?

---

### Post by Eisenwinter on 2009-01-20
Use OpenOffice.

If you're so desparate for MS Office, [wine it]("http://www.winehq.com").

---

### Post by daniel014 on 2009-01-20
I don't mind OpenOffice.org but MS Office is my prefered office suite and it is useful for compatibility at my school.

---

### Post by daniel014 on 2009-01-20
Apparently making Office on Wine is really hard and requires at lot of DLL moving, but I'll give a go. :)

---

### Post by mips on 2009-01-20
WINE or install XP in a vitual machine and then install MS Office in XP.

---

### Post by mfox on 2009-01-20
I didn't have to touch any DLLs or other files to install MS Office on Ubuntu via Wine.  With Wine already installed Office pretty much installs itself from the installation disk.  (This is Office 2003.)

---

### Post by shadylookin on 2009-01-20
> **daniel014 said:**
> I don't mind OpenOffice.org but MS Office is my prefered office suite and it is useful for compatibility at my school.

Doesn't openoffice 3 support all the MS office 2007 formats?

anyway when it comes to an OS I'm almost always using a linux based one, sometimes I try out the BSDs, and if I'm at a friends house and didn't bring my laptop I'll use windows

---

### Post by forrestcupp on 2009-01-20
Wine will install and run any Office before 2007.  If you have Office 2007, it's a little harder, but possible.  [Here is a guide](http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html) for installing Office 2007 with Wine and Crossover Games.

---

### Post by daniel014 on 2009-01-20
I've just tried copying the Program Files off of Windows Vista and running the executables in WINE but it hasn't worked.

---

### Post by Linuxidiot on 2009-01-20
What format is the file that you copied? .iso .exe ect, The reason I ask is because it helpfull to vitually mount an iso file before using the wine the wine installer.
 When i reveiwed your post you said it was because of school requirements to submit assignments. I was in your same situation and going to go through the proccess of installing MS office in wine. But what i have learned was most schools accept open office formats in version 2.4 or later. Before taking any unessecary steps, check to see if open office is supported. I prefer Linux programs over microsoft any day, but sometimes you do what you must. Hope this helps :)

---

### Post by mips on 2009-01-20
> **daniel014 said:**
> I've just tried copying the Program Files off of Windows Vista and running the executables in WINE but it hasn't worked.

That won't work, you need to install it.

---

### Post by Bölvaður on 2009-01-20
I urge you to try the comparability in open office 3.

update from ooo2 to ooo3 by:

System &#8594; Administration &#8594; System Sources
Third party software
+ Add
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
Refresh

it may autoupdate now, but as a short you can go:
System &#8594; Administration &#8594; Update Manager
Check
Install Updates

---

### Post by thisllub on 2009-01-20
> **mips said:**
> WINE or install XP in a vitual machine and then install MS Office in XP.

VirtualBox is your friend.

I keep an XP VM for Word.
Both Abiword and OpenOffice screw up the formatting of Word documents so I am stuck with this solution.

After going without Windows entirely I am going back the other way a little.
I think I prefer Outlook to any of the Linux options too although Claws is pretty good. Evolution is a pig.

---

### Post by jrusso2 on 2009-01-20
> **mfox said:**
> I didn't have to touch any DLLs or other files to install MS Office on Ubuntu via Wine.  With Wine already installed Office pretty much installs itself from the installation disk.  (This is Office 2003.)

Well I tried it with WINE and it asks for the registration number each time I start it.

---

### Post by maniacmusician on 2009-01-20
You can still be compatible with school policies while still using open standards; OpenOffice can at least read all the MS Office formats. For things that need to be printed, file format doesn't really make too much of a difference. 

For files that need to be emailed in, I'm fairly sure your teachers wouldn't complain about PDF. In fact, mine seem to prefer it. If it's something that has to be edited on a Windows computer in school, you can save it in an older MS Office format or use Google Documents (the latter is a lot easier and trouble-free). 

Even if you don't have any sort of a stance on open standards (which is fine), you still have to consider that you're going to experience performance loss when you run Windows executables under wine, and there are probably a few quirks that come along with it. It's much less stressful and annoying to simply use native tools.

---

### Post by mamamia88 on 2009-01-20
office runs great in crossover linux but that will cost you $40

---

### Post by abn91c on 2009-01-20
Open office 3.0 supports MSO 2007 formats

---

### Post by chronographer on 2009-01-20
I use open office 3 and it is fine. Just give school folks .pdf files. You can do things in OO.o that you can't do in Office, just use open office!

---

### Post by JordyD on 2009-01-20
> **daniel014 said:**
> I completely love Ubuntu but hate Windows.

Ubuntu is absolutely fine except I want to be able to use MS Office, but without dual booting.

Any help? Thanks in advance.

You can save OpenOffice.org documents as MS Office documents. In Ubuntu, when you choose "Save as..." in the File menu, at the bottom of the window, there is a drop-down that allows you to save it as an MS Office document. Just choose the MS Office version of your choice from there.

---

### Post by doorknob60 on 2009-01-20
> **daniel014 said:**
> Apparently making Office on Wine is really hard and requires at lot of DLL moving, but I'll give a go. :)

Not any more, I didn;t need to mess with much to get it working, and if you're concerned about setting it up, use Crossover Office ($40, and I think there's a free trial too). And also, I've never noticed any major incompatibilities with MS Office files (even the few 2007 ones I've opened) and OOo. I use OOo for all my stuff, but my parents prefer MS Office and it works fine for them in Wine.

---

### Post by phrostbyte on 2009-01-20
MS Office 2003 installs and runs fine in Wine.. I've done it and can confirm Word/Excel/PowerPoint work excellent.

MS Office 2007 might be a different story. But hope is not lost, as you can use something called a "virtual machine" to make Windows think it's on a real machine but it's really running on a window in your Linux workstation.

Virtualbox will do that for you. It's extremely simple.

---

### Post by sports fan Matt on 2009-01-21
my $0.02..I just came back after 6 long and pain months of blue screens, things crashing..Windows was terrible, and in my opinion, OO is the about the same thing and id never go back to MS...Even got the fiance to try Uubntu:)

---

### Post by tubezninja on 2009-01-21
Dare I suggest it?  If you want to use MS Office proper, aren't willing/aren't able to WINE, but absolutely positively want to be a "purist" and not use MS Windows in any way, then the alternative is to get a Mac and run Office 2008 on it under OS X

---

### Post by glotz on 2009-01-21
A purist would never get a mac.

---

### Post by Sorivenul on 2009-01-21
My wife is taking an online course at the moment and recently got in an argument about this with one of her professors.

 [OpenOffice 3 supports MS Office 2007]("http://blogs.techrepublic.com.com/opensource/?p=292"), and while the linked article is up for debate, OOo 3's features are not. 

I installed Office 2003 in Wine for my wife, just in case, but after submitting her first two assignments (created in OpenOffice), there have been no complaints.

---

### Post by daniel014 on 2009-01-22
I have sorted it out.

I have compared OpenOffice.org with MS Office and found that there is not much difference in features or compatibilty so OOo can definitely be my prefered Office Suite, especially as it is completely free, but I can easily install MS Office 2007 on WINE.

Having sorted that out, I can happily move to Ubuntu without having to touch Windows again. :)

---

### Post by glotz on 2009-01-22
Happy times!

---

