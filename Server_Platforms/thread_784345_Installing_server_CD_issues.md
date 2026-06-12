---
title: "Installing server CD issues"
date: 2008-05-06
forum: Server Platforms
---

### Post by Mr_Whippy on 2008-05-06
Hi all,

I tired ubuntu not to long ago and im back now and determined to make it work, however i have a slight problem i have installed desktop on a client and am now trying to install server, 

however i get a not genuine ubuntu server cd message, is there something i need to do, i burned the CD using nero on xp 64.

any help would be appreciated.

thanks.

---

### Post by NeoGreen on 2008-05-06
Where did you download the image from?  Does it give the option to install when you boot form the CD?  The image may not have the ubuntu boot up screen, but you should have hte options to install the server.  If you don't get the option, try to download it form a different site and burn it at a slower speed.

---

### Post by FakeOutdoorsman on 2008-05-06
Before you try downloading another image your should check the disc for errors.  There is an option to do that on the main menu after you insert the disc and boot up.

---

### Post by Mr_Whippy on 2008-05-06
Thanks to you both, i will try both suggestions and see where i get, i downloaded it from the main mirror in england is it conical the place that make the distro.

ill get back to you thanks again

---

### Post by Mr_Whippy on 2008-05-06
Well i ran the cd check and it said that it was not a valid ubuntu cd, being a windows type i figured this meant it thought i was not genuine not that it was faulty from the wording, so now i am redownloading from oxford uni, to see how that goes.

---

### Post by FakeOutdoorsman on 2008-05-06
Don't download yet.  The disc was faulty, but your ISO file may still be just fine.  If you're using Windows, use [md5summer]("http://www.md5summer.org/") to get the md5sum of the ISO file.  Then compare the md5sum with the ones listed on any of the Ubuntu disc mirrors, such as [here]("http://mirrors.us.kernel.org/ubuntu-releases/8.04/MD5SUMS").  If the number is different, then you know your ISO file is bad too.

If the ISO is bad, then you can use bittorrent to check your ISO and replace any bad hashes and verify the file instead of downloading a whole new big ISO file.

---

### Post by Mr_Whippy on 2008-05-06
Hi Fake, 

cheers for the tip, i have checked the iso with the md5 and it is valid, no problems there then, i have reburned the cd twice now, once more with nero on 16x burn, my drive is 48x, capable, then i also tried it with iso burner, 

im still having no joy however i am now getting a new error, which is cannot retireve file

file:///cdrom/preseed/ubuntu-server.seed.

then it ask me if i want to try again, skip or quit, i have tried the try again it takes me back to that message, i have tried to skip it then tells me that the auto installer will not function, and gives me the following message,

load debconf preconfiguration error, says its missing or failed, 

not sure what else to do, i have ubuntu desktop currently on the machine i want to use as the server so cant be a driver issue can it, any one of you fine people any more ideas.

---

### Post by FakeOutdoorsman on 2008-05-06
I'm assuming your cd burning is creating a bad disc, the computer you are attempting to install Ubuntu on is screwy, or both.  What kind of hardware (ram amount, processor) does the computer have that you are trying to install Ubuntu on?

Try a new burning program.  Many of them have verification options that checks the md5sum of the disc after it burns.  If it is successful, then you know your problem lies with the installation computer.

I hardly use Windows XP, but I know [CDBurnerXP]("http://cdburnerxp.se/") (it is free) can verify a disc after it burns from an ISO image.  Make sure to check the "Verify Data After Burn" box before burning the disc.

---

### Post by hyper_ch on 2008-05-07
for avoiding corrupted .iso downloads use torrent. It will auto-hashcheck the download.

---

### Post by jd3010 on 2008-05-07
Hi all,

had the same problem, but got it solved by installing 6.10 and then upgrading through network to 8.10. ( i do not why my old server could not install Ubuntu server edition 7 or 8)

I updated manually the sources.list file to include all links to Hardy and to dapper-updates .... and it seemed to have worked.

Hope this helps

---

### Post by Mr_Whippy on 2008-05-07
Thanks again to you all for the tips and help provided here, 

I am at work at the moment however i will try when i get home tonight, I will also post up a hardware list, the machine is an old dell pro liant(i think) server, ill come back go through everything on here and let you know how i get on.

---

### Post by Mr_Whippy on 2008-05-12
Hi all.

a big thanks to those of you that helped me out with this problem i have finally got server installed, on a different machine, so now can go on with setting up my network. 

a big thanks again for your patience and help, i think it was a hardware compatibility issue i was having, cheers steve.

---

