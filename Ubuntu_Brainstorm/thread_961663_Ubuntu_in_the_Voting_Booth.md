---
title: "Ubuntu in the Voting Booth"
date: 2008-10-28
forum: Ubuntu Brainstorm
---

### Post by martin0642 on 2008-10-28
Just making a suggestion, but due to the fact that the problem has sprung up once again I would like to suggest that the world at large could use an ultra high-security Ubuntu variant that is specifically tailored to voting in elections of all types.  The setup and requirements should be so easy/low that the distro could even be used for High School, local referendums and National level elections.

We can build the LHC, and go to the moon, and we can't pick between two people?  The fact that the US has this problem indicates to me that other, developing countries could also benefit from this, and it would put Ubuntu in front of peoples faces and instill a sense of trust in the platform.  I would like to see an Ubuntu release that came with a certified hardware list which could become a common world-wide platform for making the will of the people known.  It would also force ClosedSource providers to improve their products if they wanted to even be competitive.  You can't beat the cost of free unless your product is stellar, and in that scenario, the voters win no matter what.

I think the following suggestions would be quasi-trivial for a small and experienced dev team, and if done properly and OpenSourced there could be no actual valid reason a government could give to justify spending money on a commercial platform when they could just buy compliant hardware and use Ubuntu.  I think mostly this can be done by stripping Ibex 8.10 down to the bare minimums, or adding a few things to the server edition.

In fact, it's quite likely that once the software is defined and set by Canonical, vendors would pop-up offering hardware-only solutions ready made for electoral deployment, just like the Netbooks are doing.  

A client edition and a server edition to manage the nodes (if they choose to operate in online mode) would bring voting into the 21st century, as the likelihood of scary hacking is less likely than mistakes caused by bad design.  Making the different modes optional allows countries to tailor them to their security needs.

*LUKS or Hardware Disk Encryption
*Minimal CPU REQ (500MHz AMD Geode?  Intel Atom?)
*No keyboard access in "Voting Mode"
*Stripped GUI such as XFCE/FVWM/FluxBox
*Touchscreen Support
*Left/Right Button support for two candidate choice
*Oversized Numpad support for keying in numbers
*Text-Audio Synthesis Support for the Blind
*Split Screen formats optimized for the number of candidates
*Large Screen Support
*Large scroll bars and "Next/Back" arrows
*Review Page to see all chosen Options
*Ability to change vote directly from review page
*Option for Printer Support for Secure Paper Trail
*Option for Internet vote tallying through VPN tunnel
*Option for 3G and Wireless access to ease deployment
*Personal Review of Paper Trail before accepting it
*Reset of voting if paper trail is rejected
*Lockout/Alarm if rejection rate is to high for a single voter
*Many Modes of operation, ability to mix and match them
*Internet/Paper/CF/USB-HDD/CD-Burn/DVD-Burn/Screen Output
*Kernel Patch to log ALL machine access, all command prompts
*Kernel Patch to log ALL hardware changes, drive ejections ect.
*Kernel Patch to timestamp everything
*Allow access to NTP via SSH2 with CERTs for official time stamps
*Server able to generate and mail/email 1-Time PAD keys to individuals for online voting via SSL/SSH2
*Election "Wizard" to assist setup
*Secure Config Files to Assist Deployment via USB Key Ect. to Nodes


These are just some ideas I had rattling around, there could obviously be improvements just as 8.10 is better than 8.04.  The difference is that there is no major OpenSource portal offering a solid option in this VERY important area, and I would like to see Ubuntu fill that gap and make the world a more democratic place to live.  I've been an Ubuntu user since Feisty, and if they can apply the kind of quality improvements to voting that they have done to the OS, the world would be a better place.

I hope my idea is at least considered, even if it is ultimately rejected.

---

### Post by aysiu on 2008-10-28
No one is stopping you from making it.

---

### Post by gnomeuser on 2008-10-29
Making a voting system is a hard task, there are a ton of requirements, audits. You are welcome to try but remember that it's not just software, you hand in a complete product, all of which you have to be able to _prove_ is safe. 

We are talking a million dollar investment in research, testing, specification talks.. you are not going to do this as a single person and I would probably not recommend using Ubuntu as the base anyways since it has no certification for security. Piggybacking on already certified products like RHEL or SLES will at least give you knowledge that the underlying software has been approved and might ease your review effort (getting approved for government deployments has a strict set of standards you need to live up to - accessability, security, interfaces, storage standards and protocols)

This being said, the average diebold voting machine has run Linux for the past many years, you already have open source in the booth, the software on top is proprietary but that is the tip of the iceberg.

I don't mean to piss on your parade but this is an area where you need to know exactly what the demands are, you also need to be able to make a bid with a finished product. A voting machine is much more than sticking a random version of Ubuntu on a machine with a touchscreen and doing a quick GUI.

---

### Post by martin0642 on 2008-10-30
You both have very good points, and I have considered working on it myself in my spare time but I'm not sure my Ubuntu-Fu skills are there yet; though it might be a good way to improve them and it does intrigue me.  

The problem is that I'm more used to SystemV type stuff like OpenBSD, and Ubuntu is using a lot of stuff like Fuse and Upstart which means the manner in which I might normally accomplish something is often does not work as expected and then leads me into a severe case of WikiDrift to figure it all out.  It's fun, but not efficient.

What I am really aiming at is a start, and people often make what I consider to be an illogical argument about the potential security risks, suggesting that just because the journey is long that it should not even be started.  Thinking that way, we would not have Linux itself, or airplanes, cars and many other examples of the evolution of hard work.

People bring up all these theoretical ways to massage the system, almost all of which are way past the technical ability level of those who might exploit them, and even with these the system would be more secure than many being used today.  

I think the "world" could use a simple to implement system which is more secure than the majority of current implementations, which would only improve with time.  Ubuntu's philosophy of bringing people together seems like the kind of mindset a Voting distro would really out fourth and the paper trail I suggested goes a long way towards thwarting misdeeds.

The NSA created GemSOS, and it's accredited at the highest levels, and that would certainly satisfy that bit of the issue.  But if Ubuntu was used, then it's base components might get accredited as well, which I think is a boon for the Distro itself and might possibly allow it to make inroads against RedHat in Government and Private sectors.  

The types of accreditations needed for voting are mostly the same as for high-assurance systems.  I was under the impression that Canonical was interested in more adoption of their server distro.

I've been to a lot of countries using voting methods that are far more vulnerable to chicanery than what I am proposing even in it's infancy, and even if version 1.0 is not ready for full-on U.S. National elections, version 4 might be.  

:KSThe progression Ubuntu has made from it's initial version to the awesome 8.10 release is an example of the layer-by-layer approach which could eventually become the de-facto standard in securing democracy worldwide.  I don't even have a Windows install anymore, something that even 2 years ago would not have been viable for me.

Lastly, I don't think you need a "total" solution which includes hardware.  I think software is enough, as long as it has support for things like TPM and other hardware.  

This is because for a high-school election or Nigerian town-hall elections, a regular i686 system with the base install will do.  They don't need all the bells and whistles that the software supports.  

However, if the U.S. Government bids a contract for voting machines, a vendor might simply use the official "Votebuntu Hardware Certification List" and piece the hardware together in a proper secure housing and load the software.  Additionally, hardware vendors would clamor to get certified to get in on the Voting Machine market.  

If the distro itself was certified with everything on the HCL, it would grease the skids for more hardware vendors to make solutions, and increase competition.  It would also force companies like DieBold to either improve their options, or become a hardware only vendor.

So yea, it's not something that could be built in a day, but neither are most things worth doing.  It just seems that with the world shrinking one bit at a time it would be nice to have a widely recognized standard bearer for democracy on a global scale, available in all languages, free to help the people choose the leaders of tomorrow.  

Version by version it would gain credibility and security, and in the end it would certainly enrich the world and leave it off in a better state than when it started, even if only indirectly.  I think I'm going to take a stab at it if only for the purposes of self-education, but I thought I might out it out there in case a more capable person thought the idea had merit.

---

