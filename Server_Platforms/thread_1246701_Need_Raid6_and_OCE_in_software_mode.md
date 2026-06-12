---
title: "Need Raid6 and OCE in software mode"
date: 2009-08-22
forum: Server Platforms
---

### Post by Mech0z on 2009-08-22
Is it possible to easy setup a software raid6 with ubuntu? I only want to use the computer its running on as a NAS server and share files to windows clients (Just my desktop and laptop both running Windows 7)

I want to be able to keep adding drives (Yes I know I have to rebuild each time I add a drive) without formatting my current array of drives using OCE or is it ORLM ?

Its going to run on a AMD Phenom X3 which I hope is enough to do Raid6 software raid.

---

### Post by windependence on 2009-08-22
Don't jump on me for not suggesting Ubuntu, but there is a product out there that fits your needs perfectly and is probably smaller and more stable. Check out FreeNAS:

[http://www.freenas.org/](http://www.freenas.org/)

It's based on FreeBSD, and is easily configured from a web GUI. Version 0.7RC1 is stable enough to use IMHO and has some great features. You can do all kinds of software RAID on the box after you have it configured.

-Tim

---

### Post by Mech0z on 2009-08-22
> **windependence said:**
> Don't jump on me for not suggesting Ubuntu, but there is a product out there that fits your needs perfectly and is probably smaller and more stable. Check out FreeNAS:

[http://www.freenas.org/](http://www.freenas.org/)

It's based on FreeBSD, and is easily configured from a web GUI. Version 0.7RC1 is stable enough to use IMHO and has some great features. You can do all kinds of software RAID on the box after you have it configured.

-Tim

Well I have seen that (Cant post on their forums dont work for some reason) but from what I can see it do not have Raid6 capeabilites and I really want that as I wont be running with raid drives rated for 24/7 operations as they are twice as expensive and the WD GP drives I use now seem to work fine, but I just want more assurance using raid6 then.

---

### Post by fjgaude on 2009-08-22
Well, **mdadm** under Linux works just fine, if, and that is a big if, if you learn its ins and outs before doing things to a built array without knowing it is the correct thing to do.

You CPU will be plenty fast enough to handle a raid6 array. How many drives are you starting off with?

---

### Post by Mech0z on 2009-08-22
> **fjgaude said:**
> Well, **mdadm** under Linux works just fine, if, and that is a big if, if you learn its ins and outs before doing things to a built array without knowing it is the correct thing to do.

You CPU will be plenty fast enough to handle a raid6 array. How many drives are you starting off with?

I have 3 drives now but would buy 4 more and when the first 3s data is transferred to the new raid6 with 4 drives then those 3 drives would be added to the array. 

But you make it sound like using this mdadm is hard? I am not good at any linux based systems and have been rather happy in my 15 years with Windows, but in software raid it just dont match the capeabilities of Linux based systems.

---

### Post by fjgaude on 2009-08-22
Here's some stuff to study:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

And of course the man pages for **mdadm**.

---

### Post by windependence on 2009-08-23
> **Mech0z said:**
> I have 3 drives now but would buy 4 more and when the first 3s data is transferred to the new raid6 with 4 drives then those 3 drives would be added to the array. 

But you make it sound like using this mdadm is hard? I am not good at any linux based systems and have been rather happy in my 15 years with Windows, but in software raid it just dont match the capeabilities of Linux based systems.

You need at least 4 drives to use RAID 6. I won't get into the debate about drive failures except to say that a lot of what is being blogged about out there is a bunch of crap. I don't run little stuff. I don't run home servers. I run companies, some fortune 500 and fortune 100, and we still use all RAID 5. The MTBF of modern hard drives is 1,000,000 hours. Do you know how long that is? About 114 YEARS. Are you running a bank? Are you not going to watch the server in case you have a drive fail? The chances of two drives failing at one time are astronomical. the chances of them failing at all is slim.

BTW, the server drives (at least through my distributors) are not twice the price. What drives are you using and what are you paying. I may be able to help you or point you in the correct direction.

-Tim

VMware Partner
AMD Solution Provider
Seagate Partner

---

### Post by Mech0z on 2009-08-23
> **windependence said:**
> You need at least 4 drives to use RAID 6. I won't get into the debate about drive failures except to say that a lot of what is being blogged about out there is a bunch of crap. I don't run little stuff. I don't run home servers. I run companies, some fortune 500 and fortune 100, and we still use all RAID 5. The MTBF of modern hard drives is 1,000,000 hours. Do you know how long that is? About 114 YEARS. Are you running a bank? Are you not going to watch the server in case you have a drive fail? The chances of two drives failing at one time are astronomical. the chances of them failing at all is slim.

BTW, the server drives (at least through my distributors) are not twice the price. What drives are you using and what are you paying. I may be able to help you or point you in the correct direction.

-Tim

VMware Partner
AMD Solution Provider
Seagate Partner

I am using Western Digital GP (Green power I think) 1Tb drives a mix of those with 16 and 32 mb cache.

The reason I wanted raid6 was that if raid5 fails then the rebuild of a big raid5 takes 20+ hours where the drives will be very stressed (I guess they will, never tried it) and therefore have a bigger risk of failure in these many stressful hours, but I might just over compensating.

The 1 TB prices are here
[http://old.edbpriser.dk/Products/Listproducts.asp?ID=16&Parent=2&Sort=&Gallery=&Producent=624&Rating=0&Max=&Soegeord=&Direction24=1&Sorted24=1099511627775%2C96&Equal6914=44841&Direction27=2&Sorted27=&Direction28=2&Sorted28=&Direction25=0&Sorted25=&Direction578=0&Sorted578=&Direction2353=2&Sorted2353=&Tlist12440-93827=&Submit.x=43&Submit.y=3]("http://old.edbpriser.dk/Products/Listproducts.asp?ID=16&Parent=2&Sort=&Gallery=&Producent=624&Rating=0&Max=&Soegeord=&Direction24=1&Sorted24=1099511627775%2C96&Equal6914=44841&Direction27=2&Sorted27=&Direction28=2&Sorted28=&Direction25=0&Sorted25=&Direction578=0&Sorted578=&Direction2353=2&Sorted2353=&Tlist12440-93827=&Submit.x=43&Submit.y=3")

Where you can see the cheapest is 518DKK and the 24/7 (RE model) is 952DKK
Or 0.51DKK / GB vs 0.93DKK / GB and my 3 current 1TB drives are not the RE model.

I also considered Samsung SpinPoint F2EG as they are only 0.45DKK / GB but they seem to have a much worse record of failing compared to the WD drives.

---

### Post by windependence on 2009-08-24
Stick with the WD drives. Too bad they'd probably kill you with VAT because I could get you the good drives for about 450 DKK. With shipping and VAT they would probably be close to what you would pay. :-(

The green drives should be just fine. They have the same seek time as drives with faster rotational speed. Seek time is what counts anyway. Because of the lower rotational speed, they should also produce less heat and last longer. I am using several of these in production and I have had no issues.

-Tim

---

### Post by Mech0z on 2009-08-24
Ok I will begin reading abit about setting this up and then when I have moved from this appartment in 3 weeks I can begin looking at if I really will have the space for dedicated NAS ^^

---

