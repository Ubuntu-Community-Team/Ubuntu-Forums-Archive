---
title: "Prevent USB keyloggers?"
date: 2012-11-02
forum: Security
---

### Post by frogotronic on 2012-11-02
Hello,

  I work as an instructor at a major US university.  We are beginning to see a disturbing trend in students using USB based keyloggers to steal identifications (passwords, etc).

  In Ubuntu 12.04, is there any way to prevent USB based keyloggers from grabbing the keystrokes?

Thanks,
CH

Example of keylogger: [http://www.keysnatch.com/usbkeylogger.html](http://www.keysnatch.com/usbkeylogger.html)

---

### Post by dannyboy79 on 2012-11-02
only way I can think of is disabling USB sticks from working all together, is that an option or do these workstations require USB access?  Another tip would be for any user sitting down at a station to check that the machine does NOT have any USB sticks already plugged in.

---

### Post by drmrgd on 2012-11-02
This kind of thing just aggravates me to no end!  Because of some idiots, computer technology has become more and more difficult to use.  There are a bunch of groups here at my job, where the use of USB flash drives is completely prohibited (the USB ports are actually sealed off!), and combined with the extremely limited network (again for security reasons), moving data around (which is absolutely critical for our work) is becoming more and more of a nightmare.  

I guess it won't be long before USB flash drives are a thing of the past due to these idiots!

---

### Post by CharlesA on 2012-11-02
You could disable the USB ports, but thing thing is, people who want to do this will find a way around it.

The one you linked to needs to go between the keyboard and the computer, so you could advise students to check their PCs when they sit down at them.

The better solution would be to take it up with the school, and have them enforce a policy forbidding those devices, with disciplinary action to people caught using them.

---

### Post by mike acker on 2012-11-02
if the physical security of the machine is compromised, if you let me take the machine apart -- it's toast.

this could be the argument that puts BYOD over the top:confused:

---

### Post by Ms. Daisy on 2012-11-02
> **cement_head said:**
> Hello,

  I work as an instructor at a major US university.  We are beginning to see a disturbing trend in students using USB based keyloggers to steal identifications (passwords, etc).

  In Ubuntu 12.04, is there any way to prevent USB based keyloggers from grabbing the keystrokes?

Thanks,
CH

Example of keylogger: [http://www.keysnatch.com/usbkeylogger.html](http://www.keysnatch.com/usbkeylogger.html) Like others said, you can disable the USB ports altogether, but I imagine that's how the majority of students move their work around.  Sounds like an unacceptable solution.

You could look at kiosk-type setups. They use these in hotels and the like, they basically revert to a clean install after each user. I've never set one up, but I know there have been several threads within this forum about it. Might be worth doing a search for.

---

### Post by CharlesA on 2012-11-02
> **Ms. Daisy said:**
> Like others said, you can disable the USB ports altogether, but I imagine that's how the majority of students move their work around.  Sounds like an unacceptable solution.

You could look at kiosk-type setups. They use these in hotels and the like, they basically revert to a clean install after each user. I've never set one up, but I know there have been several threads within this forum about it. Might be worth doing a search for.
That sort of thing wouldn't prevent a hardware keylogger tho. I don't think much could, except disabling USB if it is a USB device. They probably have similar stuff for PS/2 as well, so it would be a better idea to warn students about using them and enforce the policy.

---

### Post by cryptotheslow on 2012-11-02
Options:
a. Epoxy resin the keyboard and mouse connectors into their ports. Check regularly for disturbance. Pain in the rear when the mouse or kb dies :/

b. Run the keyboard and mouse cables into the PC case and connect to internal onboard usb headers rather than use external ports. Enable case open alarms in BIOS and network trap them if that functionality is available on the kit you use.

c. Bulletin all students that systems are monitored and such interference will result in legal action. Setup CCTV, identify the culprits throw the book at them. Once one or two have been chucked in jail for a few years installing such things to grab a Facebook password or something will no longer be seen as a "prank". Internal disciplinary procedures are not enough IMHO.

---

### Post by OpSecShellshock on 2012-11-03
Yes, it's important to have policy-based monitoring and disciplinary procedures in place. But understand that still won't stop everyone. There are really 2 options: restrict access to the hardware or accept the risk. And to be honest the risk is still there even with restricted hardware access, because someone is always able to get their hands on it.

---

### Post by KaosuX on 2012-11-03
I have run into this problem before. While  it might seem like an impossible task, it is quite simple to deter for the most part. Follow these basic guidelines and you can begin the process of weeding out these types of attacks.

1. Place each computer in the class on top of the desks and not under them. Ensure that the back of the machine is visible to the instructor and/or I.T. staff upon a quick inspection. It is equally important that the front of the machine is visible to the student.

1b. Train teaching staff and students to easily and quickly identify hardware-based keyloggers and things of that nature. Print out a list of the most common devices and place them on or near each computer. Make the format something similar to: "See one of these attached to your workstation? Report it immediately!". 

1c. Work with the on-site I.T. staff and ask that they do random inspections at times that work for you. Make it known that if any malicious devices are found upon a random inspection, the attacker  risks being expelled and reported to the proper authorities.

2. Disable all unused USB ports. If this is not acceptable, purchase plastic caps used to seal off the exposed USB port. Using covers is fairly effective when the attacker has to remove one from the back of a computer sitting on a desk, in clear view of the teaching staff. 

2b. If it were me, I would disable the USB ports, place caps over the exposed ports, put everything in plain view and then require students to transfer data through free cloud services. Skydrive, DropBox, etc.

2c. In addition to 2b, I also found it useful to create a script that would create a list of all connected USB devices. If a device was detected that was not specified in a whitelist by its vendorID then it would dispatch an email to the I.T. staff and they would quickly go to inspect the machine. That would likely catch most script kiddies looking to prey on innocent students.

If you choose to use a script that emails the I.T. staff when a USB  device is detected that is not in your whitelist you will need to make  one simple modification. Allow students to have a token generated by the  I.T. staff for their personal USB devices. In this token would be  personally identifying information. The script will ignore devices with  valid tokens (checked against a database) and report invalid tokens.  Each use of any token would be logged remotely.

Now if anyone decides to use their token to connect a malicious device,  it becomes much easier to track down that person. Let students know they  are personally held accountable for any illegal activities done using  their tokens, so they are to guard them.

Those are just some highly effective ideas to help get you going. I have  personally used the token/whitelist system before and it worked like a  charm. It creates a little more work having to issue the tokens, but  goes a long way to prevent abuse.

if you really wanted to, you could take it one step further and have the  script LOCK the machine when an "unsupported" device is detected and  only allow the teaching/I.T. staff to unlock it after manual inspection.  Again, more work, but would take care of this problem.

I can help you design such a system if needed, and I have about 200  other great ideas regarding this situation. Let me know if you would  like to discuss this further with me.

3. Create strong policies that I.T. staff, teaching staff and other students are able to participate in and help improve the quality of life for everyone. Educating the users and staff is your greatest weapon in this war.

---

