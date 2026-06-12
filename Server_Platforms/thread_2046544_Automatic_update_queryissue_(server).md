---
title: "Automatic update query/issue (server)"
date: 2012-08-23
forum: Server Platforms
---

### Post by Raxje on 2012-08-23
Hi,

I've created a very basic script to run apt-get update and apt-get dist-upgrade unattended (run with cron) and save the logs. Though, it's not really a script, just a file containing the commands to run in order: [http://pasteit.com/18601](http://pasteit.com/18601)

I'm currently testing this and ran into some unexpected behavior during the recent Kernel upgrade: [http://pasteit.com/18602](http://pasteit.com/18602)

It appears the grep for the Kernel name kicked in and restarted the server before the upgrade even started. Does apt-get dist-upgrade run in the background or should the script wait for the process to finish before proceeding to the next step?

The following day it then did it correctly but in a non-test scenario it wouldn't run for another month: [http://pasteit.com/18603](http://pasteit.com/18603)

I'm basically trying to find out if this is a script error. Someone else mentioned that they checked the server the day it failed to update and apt-get dist-upgrade said there were no outstanding patches but I can't confirm this.

Any help would be appreciated!
Raxje

P.S. I realize that the -q is not required, will remove that!

---

### Post by 2F4U on 2012-08-23
Seems to me as if you are reinventing the wheel. There is already a software package for unattended upgrades available:

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

### Post by Raxje on 2012-08-23
> **2F4U said:**
> Seems to me as if you are reinventing the wheel. There is already a software package for unattended upgrades available:

[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

Hi,

Yea I was asked to look at that before but haven't gotten round to it yet. Actually one of the main reasons I have my own thing put together is because of the weird scheduling requirement on the patching.

Basically I need to patch the system on a set day e.g. Tuesday following the 3rd or 4th Monday of the month. So I currently have a cron job set to run every day from the 15th to the 21st, which will execute a script which checks if the day is Monday and if not cancel, while if it is Monday, it sets a job (the above patch script) to run on Tuesday or whatever day by using an at command (e.g. at now + 1 day).

---

### Post by Raxje on 2012-08-30
Hi,

I've tried updating the script a little: [http://pastie.org/4617054](http://pastie.org/4617054)

I then built 2 test vm's both running ubuntu 12.04 with kernel 3.2.0-23 to produce the kernel update to 3.2.0-29

The first one mirrored what happened in the OP, where it stopped because of the grep, displaying 'Kernel updates - restarting..." at the end of the log (note: none of the previous echo's were produced).

The second one worked as expected, which is odd because they were both clones of a newly built VM.

Could this be some form of bug with apt or is my script just wrong?

---

### Post by Raxje on 2012-08-31
I have uploaded 2 different logs from the same script, run on 2 different but cloned VM's yesterday

VM 1: [http://pastie.org/private/du4fyycllipkyedqyeboag](http://pastie.org/private/du4fyycllipkyedqyeboag)
VM 2: [http://pastie.org/private/wsrkedk52dkifrwxrceuoq](http://pastie.org/private/wsrkedk52dkifrwxrceuoq)

As you can see VM 2 didn't complete dist-upgrade before the script continued to the grep stage, while it worked on VM 1. This happened last week on the main test server, it simply failed to complete before the reboot.

---

### Post by koenn on 2012-08-31
> **Raxje said:**
> Hi,
(note: none of the previous echo's were produced).


yes, and that tells you what the problem is, doesn't it ? 

you have
```

sudo apt-get -y dist-upgrade >> /home/autopatch/patch_notes \
 && echo "Patching complete - Checking for Kernel update.."
```

You know that '&&' only runs the 2nd statement after the 1st has completed **successfully**, right ?

so the absence of that echo tells your 'sudo apt-get ...' did not exit with a 0 error code. 

You should trap errors there (rather than report on success only) and have your script react to them, eg. complain and exit, because your subsequent statements don't make much sense (and are potentially dangerous) if the dist-upgrade failed. Rebooting with a half-installed kernel, for instance, is not a good idea.

---

### Post by Raxje on 2012-08-31
> **koenn said:**
> yes, and that tells you what the problem is, doesn't it ? 

you have
```

sudo apt-get -y dist-upgrade >> /home/autopatch/patch_notes \
 && echo "Patching complete - Checking for Kernel update.."
```

You know that '&&' only runs the 2nd statement after the 1st has completed **successfully**, right ?

so the absence of that echo tells your 'sudo apt-get ...' did not exit with a 0 error code. 


Hi,

Thanks for the reply, very much appreciated!

I had already come to the conclusion that it was an issue with the dist-upgrade, having changed the grep to check for /var/run/reboot-required instead of the text 'linux-image' in the log. This way it's no longer rebooting in error. I then noticed when running it there were errors being produced like Hash sum mismatch or bad requests.

What you've told me has reaffirmed what I concluded earlier.

> 
You should trap errors there (rather than report on success only) and have your script react to them, eg. complain and exit, because your subsequent statements don't make much sense (and are potentially dangerous) if the dist-upgrade failed. Rebooting with a half-installed kernel, for instance, is not a good idea.

I'm afraid my bash knowledge is a bit limited but I'll try to figure this out.

Thank you!

---

### Post by koenn on 2012-08-31
> **Raxje said:**
> 

I'm afraid my bash knowledge is a bit limited but I'll try to figure this out.



it's not that hard, really
you can detect error conditions a number of ways. 

There's '$?', it's a variable that always contains the return value (a.k.a. error code) of the most recent command. You then just use if/then/else to distinguish between what to do if all is well and what to do if something didn't go as planned. The latter can include showing a message with an explanation of what went wrong, or an attempt to fix things.

if you redirect output, as one often does to log results from scripts, you should also catch error output, aka STERR. With scripts, you don't always watch the ouput on the screen, and if you redirect output to a log but don't explicitly handle STERR, you won't see the error messages

lastlly, this construction is a simple and effective way to make your script complain and exit if a command didn't complete error-free

```
wget abc.google.com || (echo "wget failed"; exit)

```

you can of course replace the 'complain and exit' part with some other appropriate action



A good bash manual will have plenty of examples on how to use this, and you can also learn a lot from looking at other peoples' scripts.

---

