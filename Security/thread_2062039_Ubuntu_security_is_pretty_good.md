---
title: "Ubuntu security is pretty good"
date: 2012-09-24
forum: Security
---

### Post by Welly Wu on 2012-09-24
Unless something unexpected happens in the future, I expect to continue to learn more about GNU/Linux and to use Ubuntu 64 bit LTS versions for the foreseeable future. I also plan to purchase another System76 notebook PC with the latest Ubuntu 64 bit LTS release at that time as I found it is much easier to work with an Ubuntu certified PC than trying to make Ubuntu install and work on a Windows certified PC.

Ubuntu security is pretty good. Here is a list of what I have done to harden my Ubuntu:

GUFW blocking all incoming traffic except for Samba and CrashPlan+ along with IPP for my Canon Pixma MX870 802.11 G Wi-Fi connected all-in-one printer
LUKS
ecryptfs
Ubuntu hardened packages
rkhunter
chkrootkit
ninja
set /home to chmod 700
disabled su for all users
Followed the official Ubuntu stricter environments settings
BitDefender for Unices Free with a free 1 year key
AppArmor profiles installed
Turned on AppArmor profile to enforcing for Mozilla Firefox
Added Open Java JRE and JDK PPAs and update them regularly
Added Oracle Java JRE and JDK PPAs and update them regularly
Installed the official Adobe Flash and keep it up to date
NoScript for Mozilla Firefox
Installed and ran tiger
Installed wireshark and check my 802.11 G WPA-2 WPA-AES-TKIP network for incoming and outgoing traffic
regularly check my logs including my Verizon FiOS router logs
Scan for viruses, root kits, trojan horses, key loggers, etc. weekly
7-zip installed and I compressed and encrypted critical user data files using AES-256
Use Deja Dup to backup my data daily
Purchased, installed, and keep VM Ware Workstation 9.x 64 bit up to date
Installed and updated Windows 7 64 bit guest virtual machine weekly
Boot the Ubuntu LiveCD and run fsck on my disk drives weekly
Check my other PCs regularly running Windows 7 64 bit
Use GnuPG to encrypt e-mail messages and my highly critical files for additional security
Check for data leakage weekly
Check the official Ubuntu security bulletins weekly
Use Linux kernel 3.3.6 currently
Use LastPass Premium with two-factor authentication using my two Yubico Yubi Keys
Use Google and Facebook two-factor authentication
Use two factor authentication for my Social Security account
Check my credit report and FICO scores weekly
Use WiTopia Personal VPN PRO to connect to random VPN gateways worldwide most of the time
Check sudoers file weekly
Limited the number of users on my Ubuntu PC
Check GRC to do a port and vulnerability scan weekly
Check my passwords using GRC and PassFault and LastPass weekly
Change my passwords randomly and regularly
Check installed PPAs weekly for software flaws and updates daily
Run software updates daily or every 8 hours
Use my PNC Bank safety deposit box to store offline data backups
Check my online accounts for suspicious activities, failed login attempts, record successful logins from different locations
Use 64 character or more complex and randomly generated passwords for all accounts
Removed unnecessary software weekly
Keep studying and taking IT certifications especially security certifications quarterly
Check my ninja logs for suspicious activities
Disabled unnecessary services and software applications on boot up
Check my Ubuntu Forums threads and board to stay up to date
Check my cell phone service regularly
Deactivate or cancel unnecessary online accounts and services weekly
Use random e-mail accounts for two-factor authentication password reset requests
Check Secunia and SecurityFocus websites daily
Subscribe to Microsoft security bulletins
Use the latest version of BackTrack Linux to do a security audit and penetration test on my Ubuntu system weekly
Delete cookies, LSOs, empty sessions and histories
Wipe data regularly using Gutmann 35 pass secure wipes for highly critical data that is no longer necessary


The only real security concern for me is the fact that I continue to use Microsoft Windows and Office for documents. I plan to upgrade to Windows 8 Pro 64 bit and Office 2013 Home Premium subscription in late October 2012. I want to stop using Microsoft products and services entirely, but this is not realistic for me. I want to stop using Microsoft products in the near future, but my future university requires me to use Windows and Office. Until I get accepted and I move onto campus, I won't know for sure if I can safely stop using Windows and Office once I begin taking courses and I go to classes on campus. If I find out that Ubuntu and LibreOffice can get the academic work done properly, then I will stop using Microsoft products or I will minimize using them as much as possible.

This is a pretty comprehensive list, but I may have missed something. I am not perfect. My security is never perfect. All software has flaws especially operating systems and software applications that access a remote network such as the Internet.

I consider myself to be pretty damn paranoid. I was hacked by the US government years ago so this is why I am so cautious today.

---

### Post by Welly Wu on 2012-09-24
I also read and consider the Ubuntu security threads and stickies weekly.

---

### Post by Welly Wu on 2012-09-24
It's late at night and I was rambling again. This usually happens. Please excuse me.

I noticed a lot of the threads in the security forum don't apply to my needs. I wonder if there is any point to either creating or installing a custom apparmor profile for vm ware workstation? I already disabled a lot of the other services that others use because I don't need them.

I need to go to sleep now. My head hurts thinking about this stuff all of the time.

---

### Post by Hungry Man on 2012-09-24
I think this forum is less about discussing our particular security setups and more for advice. Just an FYI, it may be more suited to a separate subforum.

That said, your last post does belong here.

> I wonder if there is any point to either creating or installing a custom apparmor profile for vm ware workstation?
Sure, you could. Virtual Machine exploits have happened in the past where code executed on the VM allowed code to be executed on the host system.

P.S. If you're looking to further secure your machine you may want to look at Grsecurity.

---

### Post by Welly Wu on 2012-09-24
How do I create a custom AppArmor profile for VM Ware Workstation? If possible, where can I download a pre-configured AppArmor profile for it?

---

### Post by Welly Wu on 2012-09-24
GRSecurity is not supported on Ubuntu Forums. I would like to stay away from it for now. I don't want to break my Ubuntu operating system or software applications prematurely.

---

### Post by bodhi.zazen on 2012-09-24
> **Welly Wu said:**
> Wipe data regularly using Gutmann 35 pass secure wipes for highly critical data that is no longer necessary

I did not review your entire list, but, that above is completely unnecessary and is excessive strain on your hard drive.

The Gutmann theory has been debunked.

See: [http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)

---

### Post by Welly Wu on 2012-09-24
> **Hungry Man said:**
> I think this forum is less about discussing our particular security setups and more for advice. Just an FYI, it may be more suited to a separate subforum.

That said, your last post does belong here.


Sure, you could. Virtual Machine exploits have happened in the past where code executed on the VM allowed code to be executed on the host system.

P.S. If you're looking to further secure your machine you may want to look at Grsecurity.

I researched and investigated this matter in depth and the best security practice would be to keep VM Ware Workstation 9.x 64 bit up to date with current patches and updates especially on Linux hosts. This will resolve specific VM Escape attack vectors discovered by researchers and VM Ware on a timely basis.

Furthermore, disabling Guest Isolation for drag and drop and copy and paste features in my guest virtual machine is another recommendation. VM Ware Workstation 9.x 64 bit allows for encryption of guest virtual machines and restrictions on modifications to the configuration settings for each one, but this does not address the same restrictions as a custom AppArmor profile. Moreover, disabling USB support is another recommendation if I want to prevent that class of attack vectors from compromising my guest virtual machine as well.

As it stands right now, Windows 7 64 bit does not have access to Ubuntu user data. I can not read, write, modify, or execute any data on my Ubuntu host from within my Windows 7 64 bit guest virtual machine because they are two different operating systems and file systems. I did not turn on shared folders within VM Ware Workstation 9.x 64 bit either. It is pretty much self-contained right now.

Do I have this right? Am I missing something here?

---

### Post by Hungry Man on 2012-09-24
Nope, you've got that about right. If you're looking for security I would suggest keeping the VM itself secure ie: lock that virtual Windows down.

You should look into Software Restriction Policies as well as EMET (Exploit Mitigation Enhancement Toolkit). Running both of those on your Windows VM will make local exploitation more difficult.

---

### Post by ooVoh9em on 2012-09-26
> **bodhi.zazen said:**
> I did not review your entire list, but, that above is completely unnecessary and is excessive strain on your hard drive.

The Gutmann theory has been debunked.

See: [http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)

I would say that "debunked" is a rather incorrect term to use. It is true that Gutmann's theory is no longer applicable to modern hardware, but saying it is "debunked" is like saying overwriting data itself is "debunked". Allow me to elaborate...

Gutmann's theory was only 35 passes because it would do a single pass for each type of drive encoding scheme along with hardcoded data which was best suited for overwriting whichever specific encoding type that was being wiped for that pass. Since encoding schemes would vary from drive-to-drive and it was not always a guarantee that you would be efficiently overwriting based on whichever encoding type you attempted to overwrite, it was simply easier on software developers to create a universal implementation which would target all known encoding schemes and efficient patterns for overwriting. This gave birth to a brute force approach that many commonly refer to as a Gutmann 35-pass wipe.

The security did not come from all 35 passes, but the correct combination of encoding scheme and pattern for whichever scheme your current drive was using. If you knew your exact encoding scheme then you would have been able to create software which was only using a single pass, but it would be just as secure as the original 35-passes since the single pass was efficiently overwriting your drive correctly. When a user actually ran all 35-passes only one of them was truly needed for security, rendering the other 34 passes a huge waste of time and major wear to the drive itself.

I would say the implementation of the theory was highly inefficient rather than "debunked".

With that said, using Gutmann's theory on a drive newer than 2001 is rather pointless, since drives of that era stopped using the popular encoding schemes that his paper was specifically discussing. On top of this, in 2001, drive makers introduced the Secure Erase command which was faster by a factor or two or more, and offered more substantial security.

On a modern drive your best approach would be a quick pass using a PRNG stream. It would be extremely fast, offer reliable security, and would not have a lot of extra wear on the drive. For full disk wiping, always default to Secure Erase when applicable. However, a single overwrite of zero's is also fast and reliable.

To be honest, there was nothing to really "debunk" when Gutmann's paper was released. The book you linked to was published in 2008, which was a very different time. For drives older than 2001, which were still using those specific encoding schemes, the theory worked - but the implementation was highly inefficient - specially when not too many people knew exactly which encoding scheme their drive was using.

Gutmann's theory no longer has a valid place on modern storage devices, but that was just due to a change in technology and not in a flawed theory. Like I have said several times now, it was the brute force style implementation that was flawed.

@OP

With the aforementioned already stated, you would be better off using something like shred for a quick secure erase utility for specific files. It would be faster, less wear on the drive, and offer good security. You're using a wiping method that is suppose to be used with older drives, and it is even highly inefficient with older drives it is actually supposed to be used on, unless you create a custom application which does a single pass based on the drives specific encoding scheme. It does nothing to provide you reliable security on a modern drive.

Just grab shred for single file erasures, and you will be fine. If you're paranoid, then overwrite it a few times, which is not even needed, but it might have a "feel good" factor that you are looking for.

For full disk erasure, then use Secure Erase. If using HDPARM to unfreeze the unit and erase it is scary to you, then you can grab a copy of Parted Magic, it has an easy-to-use GUI that guides you through using Secure Erase. If you still choose not to use Secure Erase, then you have other options - but most of them will waste your time on modern hardware.


A single pass offers ample protection against most forensic analysis the drive will be subject to, and likely will keep providing ample protection for years to come. If you are worried about future advancements in professional forensic recovery or extremely expensive forensic techniques deployed within high-end recovery labs, then you should just burn the drive, to be honest. However, if you want protection for years and years to come against casual forensic analysis, feel free to use more then one pass, and you can even choose to use a method which also explicitly declares that the overwrite be verified - this can give you a peace of mind.

This is not really a cut-and-dry topic, but my recommendations make sense given your personal attack vectors in relation to the data you're protecting. A common criminal won't be able to recover the data.

In the end, Bodhi is correct that you should not be using Gutmann's theory applied to modern drives - but I don't agree with his comment that the theory itself was "debunked" for the reasons explained above.

I have written a guide for a few Government facilities I have worked for with all of this information, including implementation specifics for each erasure method to demonstrate effectiveness, reliability, and other factors such as being standards compliant given a pre-defined security policy (Most require a verify mechanism) if you would be interested in reading it. I go into more detail.

Also, be aware that even if you secure erase a drive, there are other portions of the drive that these erasure methods leave untouched. While the DCO/HPA and other areas often do not contain sensitive information, it is possible for an examiner to recover data from these segments even if the drive was overwritten. While I doubt this would have a huge impact on standard users it does demonstrate that secure drive erasure is far from perfect, and should not be relied on explicitly. It works best in addition to strong encryption, to ensure maximum security against data leakage.

P.S. If you're trying to securely erase data from an SSD drive, the game changes completely. So, be ready for that when dealing with SSD drives.
Anyway, I am done. Hope this post was helpful.

---

### Post by rookcifer on 2012-09-28
> **troopa said:**
> A single pass offers ample protection against most forensic analysis the drive will be subject to, and likely will keep providing ample protection for years to come. If you are worried about future advancements in professional forensic recovery or extremely expensive forensic techniques deployed within high-end recovery labs, then you should just burn the drive, to be honest. However, if you want protection for years and years to come against casual forensic analysis, feel free to use more then one pass, and you can even choose to use a method which also explicitly declares that the overwrite be verified - this can give you a peace of mind.


What would those advances be?  MFM's are the tool for it (and I don't see how you could get much better than seeing every bit microscopically).  Researchers (Wright, Kleiman and Sundhar) back in 2008 have already tried to use MFM microscopes to recover data on drives.  It failed.  They found out that trying to determine what each bit was was essentially a coin-flip.  In other words, chance.  To make matters worse the larger the drive, the more unfeasible it was (I think they were only using like 10 GB drives or less).  They estimated it would take years to image a drive of only a few GB's and then the resulting data would be mostly useless.  The paper used to be online, but I don't have a link to it off hand.

Gutmann said in his paper that intelligence agencies "routinely recover data with MFM's."  However he didn't provide a single source in the paper for that assertion.  So, basically, he was making stuff up, [got called on it by various people]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html"), and now has had to recant (even though he still refuses to give up the idea that you need multiple passes, he just says now "3 or 4.")

The preponderance of evidence is that MFM's can retrieve bits and pieces of data here and there, but they cannot retrieve enough to make anything meaningful out of it.  Moreover, as I said, it would take *years* to image one drive.

So, basically, the notion that you can recover any meaningful data from overwritten drives is a myth.


> While I doubt this would have a huge impact on standard users it does demonstrate that secure drive erasure is far from perfect, and should not be relied on explicitly. It works best in addition to strong encryption, to ensure maximum security against data leakage.

Strong encryption is no better or worse than overwriting the drive.  What does an encrypted drive look like when looking at it with a hex editor?  It looks like random data.  That's what modern ciphers do -- they make things look random.  Therefore, it follows that if you overwrite the drive with, say, AES in counter mode (or use /dev/urandom), it would achieve the same effect as having the data encrypted.  The only difference is you wouldn't have the key.  

The only time crypto would be better is when you have a fresh drive and have encrypted the data from day one.  

> P.S. If you're trying to securely erase data from an SSD drive, the game changes completely. So, be ready for that when dealing with SSD drives.

I am eagerly awaiting Gutmann's next paper on SSD's.  "You must erase them with over 9,000 passes."  :p

---

### Post by Welly Wu on 2012-10-01
I am going to re-read and apply the Ubuntu Security sticky's recommendation to look into toward a moderately paranoid Debian installation later today.

I think that I am doing most of the things right for security.

What else should I read and consider implementing?

---

### Post by mike acker on 2012-10-01
if you need to insure the disk content is destroyed: destroy the disc physically. a 5 lb engineer's hammer should suffice.

---

### Post by NadirPoint on 2012-10-01
> **mike acker said:**
> if you need to insure the disk content is destroyed: destroy the disc physically.
No doubt.  What's with the OCD WRT data destruction?

.45 ACP ball is quick, easy and even fun if you get into that sort of thing.  :P

---

### Post by Welly Wu on 2012-10-01
I just added integrit and OpenVAS along with logwatch and logfail.

---

### Post by Welly Wu on 2012-10-02
I just added fail2ban.

---

### Post by Welly Wu on 2012-10-02
I just created a Novell AppArmor profile for wineserver and wine-preloader. I don't have any WINE software applications installed yet because I use Codeweavers' CrossOver for Linux 64 bit.

---

