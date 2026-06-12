---
title: "Does formatting a USB drive remove all viruses?"
date: 2012-07-02
forum: Security
---

### Post by aligator12 on 2012-07-02
Hay guys, I have an old USB thumb drive that was used a while back on a few infected Windows machines, I was wondering, if I format the drive in Ubuntu, does that completely remove any malware on it?

---

### Post by Wiebelhaus on 2012-07-02
Yes, absolutely. 100%.

---

### Post by aligator12 on 2012-07-02
> **Wiebelhaus said:**
> Yes, absolutely. 100%.
Is there any damage this malware could do to my ubuntu machine?

---

### Post by robtygart on 2012-07-02
Not if it comes from or made for a Windows computer.

---

### Post by aligator12 on 2012-07-02
> **robtygart said:**
> Not if it comes from or made for a Windows micheen.
Just out of curiosity, is there any known malware that -by just inserting- a USB drive into an ubuntu machine could lead to it being compromised?

---

### Post by Wiebelhaus on 2012-07-02
> **aligator12 said:**
> Just out of curiosity, is there any known malware that -by just inserting- a USB drive into an ubuntu machine could lead to it being compromised?

No, that's why computer techs often use some form of linux to cleanse the filth from windows machines, your doing it right.

---

### Post by HermanAB on 2012-07-03
You should also wipe the device with a disinfectant like Lysol.  With Windows, you don't know where it has been...

---

### Post by xedi on 2012-07-03
If you want to be extra safe (even though as the others suggested this is probably unnecessary), you could also login as guest or use a ubuntu live cd.

---

### Post by kurt18947 on 2012-07-03
I don't know if it matters but I'd probably use Gparted.  Remove the partition entirely, repartition then reformat.  I think but am not certain that removing the partition would also overwrite the MBR in case an MBR infection were present.  I don't think just reformatting does.

---

### Post by bodhi.zazen on 2012-07-03
> **Wiebelhaus said:**
> Yes, absolutely. 100%.

Formatting does not over write files, you have to use dd or scrub to remvoe malware.

---

### Post by SeijiSensei on 2012-07-03
Once upon a time there were boot sector viruses that could persist through a format.  I haven't seen anything like that in years, though, nor are there likely to be any that would affect Linux.

---

### Post by lisati on 2012-07-03
> **bodhi.zazen said:**
> Formatting does not over write files, you have to use dd or scrub to remvoe malware.

Good catch. A simple "quick format" will overwrite the device's directory structure while leaving the data areas untouched, thus leaving the possibility of nasty stuff being recovered if you ever choose to practice your data recovery skills.

---

### Post by aligator12 on 2012-07-04
So I reformatted the drive with ext4, would that have wiped anything? And how do I clean the MBR?

---

### Post by Soul-Sing on 2012-07-04
yeah, [COLOR="Red"]quick and slow format[/COLOR]. But are these "options" build into Ubuntu? And indeed a quick format isn't enough to wipe all files/direct.

cleaning mbr is afaik rather difficult, maybe impossible, because you'r left with an unbootable system/harddisk.

---

### Post by aligator12 on 2012-07-04
Alright, I used "Disk Utility" to change the Partitioning from MBR to GUID back to MBR again, would that have wiped anything?

---

### Post by kurt18947 on 2012-07-04
This might be of interest:

[http://superuser.com/questions/329467/how-to-see-if-usb-stick-has-mbr](http://superuser.com/questions/329467/how-to-see-if-usb-stick-has-mbr)

---

### Post by ottosykora on 2012-07-06
formating of an usb flash will definitely not destroy all data on the flash.
Using wipe functions or some overwriting with dd will overwrite the just at that time accessible part of the flash chips, but will leave the rest of spare blocks and exchanged blocks used by the wear leveling as they are. The data will also remain in it. The just in that moment inaccessible part of the flash is often in the order of 30% but sometimes 50% of the whole size.

OK, we can not access this areas simply with our operating systems, therefore we can not delete it it or overwrite it, but enough test software circulating in net can do so however.

There is no reason why 'properly' designed malware should not use this feature of the flash  and hide in the just currently inaccessible part and act from there.

---

### Post by ottosykora on 2012-07-06
> **aligator12 said:**
> So I reformatted the drive with ext4, would that have wiped anything? And how do I clean the MBR?

did not overwrite anything on the files

with dd one can overwirte the mbr too

---

### Post by msammels on 2012-07-06
They call dd "Destroy Disk" because you can overwrite everything :)

---

### Post by Grenage on 2012-07-06
> **ottosykora said:**
> formating of an usb flash will definitely not destroy all data on the flash.
Using wipe functions or some overwriting with dd will overwrite the just at that time accessible part of the flash chips, but will leave the rest of spare blocks and exchanged blocks used by the wear leveling as they are. The data will also remain in it. The just in that moment inaccessible part of the flash is often in the order of 30% but sometimes 50% of the whole size.

OK, we can not access this areas simply with our operating systems, therefore we can not delete it it or overwrite it, but enough test software circulating in net can do so however.

There is no reason why 'properly' designed malware should not use this feature of the flash  and hide in the just currently inaccessible part and act from there.

The data would have to be in an executable format, and would have to be called in some way.  As such, malware could potentially access such data as it became available, but it can't just sit there and suddenly run itself (or indeed, be in any shape to be run).

Unallocated data is inert, no?

---

