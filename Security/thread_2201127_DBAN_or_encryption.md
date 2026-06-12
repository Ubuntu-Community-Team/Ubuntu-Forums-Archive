---
title: "DBAN or encryption?"
date: 2014-01-22
forum: Security
---

### Post by Andrew_Lucas on 2014-01-22
Hi all,

First thing first - this cloak and dagger stuff is usually a bit beyond me, so I get the feeling I'm using a sledge hammer to crack a nut. However...

Someone I know has had a lot of problems at work (I'm hesitant to give out details in the public sphere), suffice to say, it's a sensitive sector, and there's a good deal of corruption on behalf of both key individuals and the company on a wider scale. This 'person I know' has had to modify their lifestyle (again, I'm being cautious about detail) in significant ways because of this.

Recently, the company asked for a laptop previously given to be returned. I don't know what the usual procedure is regarding this, but AFAIK, no paperwork was signed, no deposit was given, etc. The employee is in active and open conflict with the employer, and has taken/is taking legal advice, but they are insistent on the return of the machine.

Given that, the employee feels compelled to return the machine. However, their (gender neutral singular) fear is that the machine may be tampered with after its return, in an attempt to 'frame' and 'discredit' the employee. I've no idea how realistic that fear is, but I was asked about how to eliminate such a risk.

My first response was simple: DBAN. As I thought, and as the website says, although no *guarantee* is given, providing it works, no forensic method will be able to recover data. However, it will be obvious that this was done by the employee/on the employee's behalf, and to defend themselves (as above) against accusations of covering anything up, my advice would be to simply say that DBAN was used to protect private data (being as vague as possible). If pushed, and asked *what* private data, I'm going to suggest the employee states 'data that is inevitably accumulated through use of any machine, such as data on browsing habits'. To emphasise that this is actually important data, Google are in the process of being sued in my jurisdiction (the UK) over breaking Safari's 'don't track' functionality.

That was earlier this evening. I've realised another way of achieving the same ends would be to use entire disk encryption, but that would be troublesome since I know virtually nothing about encryption (presumably, there are numerous algorithms etc, and I'd have to research to choose one), and given threads such as [this]("http://ubuntuforums.org/showthread.php?t=2201054"), it seems DBAN is the more effective method anyway. It's certainly easier - providing the BIOS isn't locked down, it's just a case of boot into DBAN and let it do its thing, right?

My question is: what are the full list of alternatives, and given the situation, what would you do? I've yet to see the machine, but I'm assuming it's going to be running Windows 7 at best, probably more likely to be XP or Vista (isn't support for XP about to end? That could be the reason they want it back?). Also, if anyone has information on the following, it would be appreciated:

1) The legality of using DBAN to protect data on a *non-personal-use* machine (this needs to be related to the UK),
2) How long DBAN would take (very difficult to estimate, I know, but I'm guessing a minimum of at least 4 hours, possibly up to 24...with the weekend coming, that's not such a problem, since it's unlikely nothing will be done before Monday).
3) If there's any programs which could basically do a 'reverse DBAN'...something I could use to verify that DBAN had actually done it's job?
4) Last but not least...what (if any) special conditions I should attach to my DBAN use, i.e. how many passes, would it be a good idea to mirror the hard drive using CloneZilla first, and keep a copy of this, unbeknownst to the employer? 

Final point - another advantage of me using DBAN would be that it would mean I was engaged in as trivial as possible way: I wouldn't have access to any sensitive data which may or may not be on the computer, I wouldn't need to know any passwords etc. either. Clearly, this is preferable for me personally, though it makes seemingly little difference to the employee.

Thanks!

---

### Post by Dave_L on 2014-01-22
I can't address any legal issues, but the last time I returned a computer to my employer I wiped the hard disk and then did a fresh install of the operating system.

As I recall I used CopyWipe:
[http://www.terabyteunlimited.com/copywipe.php](http://www.terabyteunlimited.com/copywipe.php)

In this case the employer wouldn't have cared that I wiped the disk, since they routinely do that anyway on returned computers. But if someone had complained that I wiped the disk, I could just said that I wanted to make sure that no private information, either mine, the employer's or the customers', was left unsecured.  Or I could have just feigned ignorance: "The disk has no data? That's odd. I have no idea why."

---

### Post by ian-weisser on 2014-01-22
In several organizations I have been in, it's standard practice to wipe and reimage returned laptops. Several reasons: Update to latest image, prevent legacy malware, wipe old user settings and data, etc.

Lawyers are good at figuring out neutral terms for returning property with assurance against damage. Let them do their job.

---

### Post by QIII on 2014-01-22
Say you DBAN and reinstall a Windows OS.  Whatever forensic evidence may be removed except this:  it will be clear what license key was used to install it (there are tools for that) and it will be obvious that the machine was cleanly reimaged.   That will surely raise suspicious eyebrows.   Why is the key different and why was it wiped? 

In any case there is no way around clever framing after someone else has physical control of the machine.

In that case, the "person you know" will need a lawyer.  If there is something incriminating or discrediting found if the disk is not re-imaged, the "person you know"  will need a lawyer.  If there is nothing there, that needs to recorded and that will involve a lawyer.

You also left discoverable evidence here of your involvement in potential wrong-doing, so you will need a lawyer.

You get the picture.

This is a legal matter, not a technical one.

Since this is not a legal advice forum and none of us is qualified to give same,  thread closed.

---

