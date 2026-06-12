---
title: "Laptop Recommendations"
date: 2014-02-09
forum: The Cafe
---

### Post by carl4926 on 2014-02-09
Looking for any recommendations for a Laptop. Must run Ubuntu:

i7 core pref
8+ GB RAM
1TB+ HDD
Intel GPU would be fine (not hybrid though)
Doesn't need any OS pre-installed
If EFI: Known to be friendly/OK

---

### Post by pqwoerituytrueiwoq on 2014-02-09
anything wrong with the system76 laptops? link in your own signature

---

### Post by carl4926 on 2014-02-09
They are on my list of possibilities obviously

---

### Post by Old_Grey_Wolf on 2014-02-09
**Do you have a budget?**

I think you will find it difficult to find a new computer that doesn't use EFI/UEFI/Secure boot. You will have to check out what it takes to get around it for each model.

I have had succes with DELL laptops over the years; however, I did order laptops with compnent I knew would be compatible with Ubuntu/Linux. However, I don't use DELL for desktops or servers.

---

### Post by mastablasta on 2014-02-10
i would start at ubuntu certified page.
and then focus on HP, Dell, Lenovo from bigger brands.

---

### Post by bc.haynes on 2014-02-10
Mastablasta,
Whereis the Ubuntu Certified Page?  Ben

---

### Post by overdrank on 2014-02-10
> **bc.haynes said:**
> Mastablasta,
Whereis the Ubuntu Certified Page?  Ben

[_[U]ubuntu.com/certification/_[/U]]("http://www.ubuntu.com/certification/") :)

---

### Post by bc.haynes on 2014-02-10
Need to take Lenovo off the list. Tried to buy a nice Ubuntu computer, and they said they did not have any.

---

### Post by pqwoerituytrueiwoq on 2014-02-10
as far as i know ubuntu tends to run good on most leveno laptops, they just don't support it

---

### Post by masdeal on 2014-02-10
> **overdrank said:**
> [_[U]ubuntu.com/certification/_[/U]]("http://www.ubuntu.com/certification/") :)

Thanks for recommendation.... :)
Btw, I have a laptop (ASUS) with dual core processor. Can I using Ubuntu?

---

### Post by buzzingrobot on 2014-02-11
Take the Certified Hardware list as a good thing if a laptop you are considering is listed there.  Don't take it as necessarily a bad thing if it isn't. It's unclear to me how often the list is updated, if it still is.

If you are going to dual boot with Windows, then you need to avoid machines that have garnered publicity for being difficult to manage in that scenario.  The "Absolute Beginners" section here is one place to look for bad dual booting experiences.

Most laptops have hybrid video, that is, an onboard Intel video chip works in tandem with a separate chip from Nvidia or AMD that handles high performance needs. A machine that lets you choose between the Intel only, the Nvidia/AMD only, or the hybrid Intel plus Nvidia/AMD scenario is more convenient in Linux.

Don't buy a laptop you know contains components that don't work in Linux. If you buy directly from the vendor -- e.g., at Lenovo online or Dell's site -- you can select from the range of available component options on offer.

Usually, hardware that's a bit behind the bleeding edge plays better with Linux than the newest toys.

---

### Post by mastablasta on 2014-02-12
> **bc.haynes said:**
> Need to take Lenovo off the list. Tried to buy a nice Ubuntu computer, and they said they did not have any.

> **pqwoerituytrueiwoq said:**
> as far as i know ubuntu tends to run good on most leveno laptops, they just don't support it

pqwoerituytrueiwoq is correct. this means they do not have many if any with ubuntu preinstalled. however here and in many other coutnries they sell plaptops with no OS preloaded (or it has FreeDOS) and one can simply install linux on many of those. when i searched for mine i eventually decided for HP that had windows 7 starter preloaded (htough it hsould have had Home as ram can go up to 8 GB and starter only supports max 2GB). however i would have bought lenovo (sold with no os) but it's battery was much weaker and i couldn't find a better one not even 3rd party one. and battery was more important than frame and USB 3.0. most peple complained about that battery. so now the small HP has dualboot :-)

> **masdeal said:**
> Thanks for recommendation.... :)
Btw, I have a laptop (ASUS) with dual core processor. Can I using Ubuntu?

depends on other specs. GPU, wi.fi, backlight, touchpad and sometimes SSD are the ones with compatibility issues.
luckilly there is an easy way to establish if you can run it or not,
download latest 64bit (AMD64 image), burn it to DVD or USB (using netbootin) and then boto from the media. if all goes well system should boot up, loaditself to RAM and you will get an option to try it (called live OS). so you can try it see if everything works. if it doesn't post here int he forums and we can troubleshoot. solutions are often easy to find. but if everyhtign works you can install if to disk if you want to.

changes are lost on reboot from such try it session. that is unless you do some disk changes on purpose (delete files etc...).

---

### Post by buzzingrobot on 2014-02-12
If someone wants actual support for Linux from a hardware vendor, that effectively limits the choices to small specialist firms like System76 who pre-install Linux on OEM hardware. 

I'd also look carefully at the specific support these vendors provide to an end-user. 

In any case, my ThinkPad W530 has worked just fine with any Linux distribution I've thrown at it. I deleted Windows, turned off safe boot and turned on legacy BIOS boot.  All's been well.

---

### Post by mastablasta on 2014-02-12
that is not true.

Dell sells laptops with Ubuntu linux preloaded here. there is also Dells XPS developer's edition whcih is also ubuntu equipped. HP sells some mashcines with suse linux preloaded (Ubuntu usually works fine on them). these two are one of the biggest manufacturers.

when visiting Asia i saw Asus (or was it Acer) with Linpus preinstalled, there were also Lenovo with Ubuntu.

so there are big brands that have linux on their mashcines. problem is they oftenly do not have it on latest hardware models. appart form Dell and smaller ones like System76 i haven't seen linux on new hardware.

---

### Post by QDR06VV9 on 2014-02-12
Just My 2 cents worth Been Running A Lenovo B-570 and Accer 5750 Lappys
And They both work quite nicely, They have handled every distro I have thrown at them
with ease and excellent preformance.

---

### Post by buzzingrobot on 2014-02-12
> **mastablasta said:**
> that is not true.

Dell sells laptops with Ubuntu...

I didn't mention Dell given its reputation for on-again, off-again Linux sales.  Dell.com does show the XPS 13 with Ubuntu 12.04.

---

### Post by mattlach on 2014-02-12
Honestly, 

I have run Ubuntu (or one of its derivatives) on every Laptop I've owned, and never run into any problems...

---

### Post by masdeal on 2014-02-12
> **mastablasta said:**
> 
depends on other specs. GPU, wi.fi, backlight, touchpad and sometimes SSD are the ones with compatibility issues.
luckilly there is an easy way to establish if you can run it or not,
download latest 64bit (AMD64 image), burn it to DVD or USB (using netbootin) and then boto from the media. if all goes well system should boot up, loaditself to RAM and you will get an option to try it (called live OS). so you can try it see if everything works. if it doesn't post here int he forums and we can troubleshoot. solutions are often easy to find. but if everyhtign works you can install if to disk if you want to.

changes are lost on reboot from such try it session. that is unless you do some disk changes on purpose (delete files etc...).

Thanks for your tips  @mastablasta.... :)

---

### Post by carl4926 on 2014-02-13
Some great feedback - thank you

---

### Post by pqwoerituytrueiwoq on 2014-02-13
> **masdeal said:**
> Thanks for recommendation.... :)
Btw, I have a laptop (ASUS) with dual core processor. Can I using Ubuntu?
model? my A54C-NB91 matches that description and it works wonderfully with the 3.13 kernel, minor backlight kinkiness though (it does work)

---

### Post by marshall-marca on 2014-03-08
[http://www.walmart.com/ip/Acer-Cherry-Red-15.6-E1-572-6829-Laptop-PC-with-Intel-Core-i5-4200U-Processor-6GB-Memory-1TB-Hard-Drive-and-Windows-8.1/34334437](http://www.walmart.com/ip/Acer-Cherry-Red-15.6-E1-572-6829-Laptop-PC-with-Intel-Core-i5-4200U-Processor-6GB-Memory-1TB-Hard-Drive-and-Windows-8.1/34334437)


I purchased this laptop 2 days ago specifically to install Ubuntu 13.10 on it. I did a 64bit OEM install and everything installed smoothly. I did a fresh install of Ubuntu only and totally wiped the hard drive upon unboxing it. So far I have updated it to Ubuntu 14.04 and everything is working fine so far. I installed Steam and I have 4 games that were ported over to run natively on Linux and I am impressed with the Intel graphics. I recommend using Ubuntu 14.04 they have really made great progress using the Intel graphics and the games I have tested have all ran fine on max settings. I'm sure the 4th generation core i processor is a big help as well. For $500 the laptop actually runs Ubuntu very well. I have managed to get Netflix working with the help of a tutorial that I found on the forums. I was actually considering getting a Toshiba with similar specs but that model was out of stock and I am happy that I spotted this Acer because I had no issues at all with the hardware working with Ubuntu.

---

### Post by leclerc65 on 2014-03-08
I bought this

[Chromebook]("http://store.acer.com/store/acerna/en_CA/pd/productID.292521900/parentCategoryID.64661400/")

Dual boot with Ubuntu 13.10 (Chrubuntu). Both ChromeOS and Ubuntu (with Gnome-fallback) are quite snappy.
Give this one consideration if size and price are top priority. I will use it for travel instead of my iPad.

---

### Post by monkeybrain20122 on 2014-03-08
> **mastablasta said:**
> that is not true.

Dell sells laptops with Ubuntu linux preloaded here. there is also Dells XPS developer's edition whcih is also ubuntu equipped. HP sells some mashcines with suse linux preloaded (Ubuntu usually works fine on them). these two are one of the biggest manufacturers.
.

However I read that Dell's Ubuntu are not the same as the standard .iso that we install from. According to these people Dell's Ubuntu laptops use hardware components that may not be compatible with Linux and require special Dell drivers. As a result there is no guarantee that OS update will work, and even reinstalling the same Ubuntu release from ordinary channel may be problematic (let alone installing other Linux OSes). I have not had one so I am not sure if this is true or just a rumour, but on the Ubuntu hardware certified list there is a category that says certified only for OEM versions of Ubuntu (hence it is kind of misleading to say such hardware are compatible). I think one should do some research before dishing out big bugs for these.

---

### Post by adam38 on 2014-03-09
my friend says dell works best with ubuntu

---

