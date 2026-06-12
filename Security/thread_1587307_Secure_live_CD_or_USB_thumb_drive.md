---
title: "Secure live CD or USB thumb drive?"
date: 2010-10-03
forum: Security
---

### Post by ubuntu1sttimer on 2010-10-03
Have not found this elsewhere so here goes. 

I had a friend ask how he could do his electronic banking without a chance of any information being left on his computer once he is done. 

I thought of a Ubuntu live CD but have seen the HD activity light flashing when using one. That leads me to believe that some kind of use is made of the HD and that makes a live CD questionable. He wants no information on the HD even in unassigned sectors.

Maybe, better yet would be a USB thumb drive that runs Ubuntu or another distribution that will not use the HD or even require that one be in the computer. A plus with a thumb drive would be that it would only be available on the computer when it is being used so it could contain passwords etc. Of course, it would have to be removed when not in use.

There may be other ways of doing this. Your ideas are invited.

---

### Post by bodhi.zazen on 2010-10-03
Live CD is probaly not the best approach as the OS would be out of date, and thus more vulnerable then a standard install.

I suggest :

1. Secure the browser.

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

2. use NoScript.

3. Be aware of Phishing.

4. Use Private browsing. Private browsing will be sufficient for 99.9999 % of users.

5. If you want to "clean" you session after, use bleachbit.

---

### Post by BkkBonanza on 2010-10-03
I don' think the LiveCD mounts the local hard disk by default. So if there is activity it may be that it found and mounted a swap partition. You could disable that with,

sudo swapoff -a

and see if any further access is made to the hard disk. Also you can use the **mount** command to see whether any drives are mounted. And **umount** command to unmount them. Nothing can be left behind once the partition is unmounted.

---

### Post by HermanAB on 2010-10-04
Use a Linux or Windows LiveCD.

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by snowpine on 2010-10-04
bodhi.zazen's advice is right on as usual, to which I would add:

6. Contact your bank's fraud department and ask what they will do to protect you if your account is compromised. If you are not satisfied with their answer, switch banks.

---

### Post by ubuntu1sttimer on 2010-10-04
Thank you all for your comments. First, as I understand, he has talked to his bank and they will, under most cases, cover his losses. However, he would rather avoid it than the chance that he will have to go through the process involved in a loss.

The idea in a live CD or USB stick is that he can use it either on his desktop or laptop without having made changes to harden either.  

Among other problems, his bank had began a charge for mailed statements. In order to obtain more favorable terms for accounts,they require a number of hoops be jumped through. Failing any of them reverts to much poorer terms on the account. Presumably they are hoping that customers will mess up on one of the requirements and lost the advantage to the account. Also, most customers will not go to the trouble to change to a different type of account or bank and thus the bank will gain an financial advantage from their policies. Many banks in the US are now moving in this direction.

Thus, the desire to have a simple and safe way to access one's banking records without incurring fees and/or dropping out of a benificial banking plan.

So much for explaining the background of the request. The concern is that there will be information remaining on the computer when he logs off his bank web site. For example, access information or a copy of reports that he printed out. This is the reason for possible use of a live CD or USB stick. This way, if he were not to go to any other web sites and he has not written anything to a hard drive, he should not have picked up problems that could create a problem. 

BODHI.ZAZEN, thanks for the list of things to use to harden a linux computer. It gives me some ideas of what I should do as a way to protect myself while browsing and shopping on the web. Although, the above mentioned live CD would be good for shopping. If the OS on the CD was somewhat out of date, it should not be too big of a problem as, if used correctly, the user would only be going to one site. This assumes that the OS is started, there is a fairly brief visit at the desired web site, and the computer is shutdown. If some unwanted intrusion occurs, it will be gone when the computer is shut down.

If there is a problem with this idea I would be interested in it. If no problem and such a live device does not exist, it would be a good project for Ubuntu.

---

