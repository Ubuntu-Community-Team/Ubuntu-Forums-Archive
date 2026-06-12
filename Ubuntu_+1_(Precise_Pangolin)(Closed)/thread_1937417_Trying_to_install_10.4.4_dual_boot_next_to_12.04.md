---
title: "Trying to install 10.4.4 dual boot next to 12.04"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by swright007 on 2012-03-07
I tried to install 10.4.4 next to 12.04 and when the partitioning screen came up in the installer, I picked that I wanted it to use the "largest continuous free space" for the install.   It crashed telling me that there were already too many "primary" partitions on the table.

When I tried choosing the "install next to precise" option it tells me it needs to save current settings and that the resize operation might take some time.   

so far I have a 250 GB HD set up in this manner 

11 GB formatted as FAT just for storage
and 12.04 installed in a 118 GB partition
 
That leaves 118 GB free space (no partition).

Did I pick the wrong option?  Should I go with the "install next to" option and trust it ?   

I just decided I needed a stable operating system to pick occasionally until this gets release solidly.
  
I appreciate any suggestions  :)

Scott

---

### Post by ventrical on 2012-03-07
> **swright007 said:**
> I tried to install 10.4.4 next to 12.04 and when the partitioning screen came up in the installer, I picked that I wanted it to use the "largest continuous free space" for the install.   It crashed telling me that there were already too many "primary" partitions on the table.

When I tried choosing the "install next to precise" option it tells me it needs to save current settings and that the resize operation might take some time.   

so far I have a 250 GB HD set up in this manner 

11 GB formatted as FAT just for storage
and 12.04 installed in a 118 GB partition
 
That leaves 118 GB free space (no partition).

Did I pick the wrong option?  Should I go with the "install next to" option and trust it ?   

I just decided I needed a stable operating system to pick occasionally until this gets release solidly.
  
I appreciate any suggestions  :)

Scott

  I have a 500GB SATA HDD and I installed Maveric 10.10 a while back. I chose "Install Next to" and it worked just fine.

I have 3 installs of Beta1 Precise also on same drive.

 If you do this , make sure after you install Lucid that you may have to go to your Precise Install and use :
sudo update-grub
after you updated your copy of Lucid because it will not always set the kernel version from the most recent install.

---

### Post by cariboo on 2012-03-07
Manual partitioning works well too.

---

### Post by swright007 on 2012-03-07
That didn't work either.  I got the same "Too many primary partitions error".  I restarted the install program, this time picking the manual partition option.  I manually picked where I wanted the install to go and that seems to be working.  I still have my fingers crossed.     






"Use the Force, Luke.  Let it guide your actions"- OB1 Kenobi -- Star Wars

I would still feel better if the Force had some instructional videos on Youtube.

---

### Post by ventrical on 2012-03-07
> **cariboo907 said:**
> Manual partitioning works well too.

and there it is :)

---

### Post by swright007 on 2012-03-07
Yes.. that worked quite well.  Thank you... all of you.   :)    Now I can test the 12.04 and have a functional base to compare it to.  Thanks again :)

Scott

---

### Post by jerrylamos on 2012-03-08
> **swright007 said:**
> Yes.. that worked quite well.  Thank you... all of you.   :)    Now I can test the 12.04 and have a functional base to compare it to.  Thanks again :)

Scott

I have best luck with "gparted' and arranging my partitions ahead of time.  I can handle primary, secondary, ... whatever that way.

I know that doesn't test the other install partitioning options - each of my test pc's has several installs, a couple have Windoze....7, and I sure don't want ubiquity partitioning messing around and scewing things up.  I've got a ubiquity Beta bug already, $950167, as it is.

Enjoy.

Jerry

---

### Post by jerrylamos on 2012-03-08
> **swright007 said:**
> Yes.. that worked quite well.  Thank you... all of you.   :)    Now I can test the 12.04 and have a functional base to compare it to.  Thanks again :)

Scott

I have best luck with "gparted' and arranging my partitions ahead of time.  I can handle primary, secondary, ... whatever that way.

I know that doesn't test the other install partitioning options - each of my test pc's has several installs, a couple have Windoze....7, and I sure don't want ubiquity partitioning messing around and scewing things up.  I've got a ubiquity Beta bug already, $950167, as it is.

Enjoy.

Jerry

---

