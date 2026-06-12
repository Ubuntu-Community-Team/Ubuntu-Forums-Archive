---
title: "LibClamAv Warnings/Errors"
date: 2022-07-01
forum: Security
---

### Post by norahlo on 2022-07-01
Installed Ubuntu 20.04.4 LTS (focal fossa) a few days ago over Windows 8 on fam's old XPS 2720 via USB. Wasn't totally sure whether to post here or in the New to Ubuntu forum. Hopefully this is the right place for this. But I am indeed new to Ubuntu and not very techy in general so please keep this in mind when explaining or offering suggestions.

Trying to scan the entire drive with ClamAV. Running clamscan starts with [highlight][color=black][font=courier new]LibClamAV Warning: cli_scanxz: decompress file size exceeds limits[/font][/color][/highlight]. Then it's mostly [highlight][color=black][font=courier new]LibClamAV Warning: fmap_readpage: pread fail: asked for #### bytes @ offset #, got 0[/font][/color][/highlight] where the #'s vary slightly, strewn with [highlight][color=black][font=courier]LibClamAV Error: fmap_readpage: pread error: [Various][/font][/color][/highlight], "Various" being [highlight][color=black][font=courier new]No data available[/font][/color][/highlight], [highlight][color=black][font=courier new]Input/output error[/font][/color][/highlight], [highlight][color=black][font=courier new]Operation not supported[/font][/color][/highlight], [highlight][color=black][font=courier new]Invalid argument[/font][/color][/highlight], and [highlight][color=black][font=courier new]No such device or address[/font][/color][/highlight], but mostly [highlight][color=black][font=courier new]Input/output error[/font][/color][/highlight].

Like this
```
$ clamscan -r -i /
LibClamAV Warning: cli_scanxz: decompress file size exceeds limits - only scanning 27262976 bytes
LibClamAV Warning: fmap_readpage: pread fail: asked for 4094 bytes @ offset 2, got 0
LibClamAV Warning: fmap_readpage: pread fail: asked for 4094 bytes @ offset 2, got 0
LibClamAV Warning: fmap_readpage: pread fail: asked for 4094 bytes @ offset 2, got 0
LibClamAV Warning: fmap_readpage: pread fail: asked for 4094 bytes @ offset 2, got 0
[...
 etc
 ...]
LibClamAV Error: fmap_readpage: pread error: No data available
[...
 ...]
LibClamAV Error: fmap_readpage: pread error: Input/output error
[...
 ...]
LibClamAV Error: fmap_readpage: pread error: Input/output error
[...
 etc
 ...
 ...]
LibClamAV Warning: fmap_readpage: pread fail: asked for 4069 bytes @ offset 27, got 0
LibClamAV Warning: fmap_readpage: pread fail: asked for 4069 bytes @ offset 27, got 0
LibClamAV Warning: fmap_readpage: pread fail: asked for 4082 bytes @ offset 14, got 0
LibClamAV Warning: fmap_readpage: pread fail: asked for 4092 bytes @ offset 4, got 0
```
It ends there each time, without a summary or the prompt reappearing. At that point, ctrl+c to cancel clamscan doesn't work either, although it does if I do it earlier during the scan.

Incremented [highlight][color=black][font=courier new]--max-filesize=#n[/font][/color][/highlight] several times but that [highlight][color=black][font=courier new]cli_scanxz: decompress file size exceeds limits[/font][/color][/highlight] warning still results&#8288;—even at 3900M. Ran it with [highlight][color=black][font=courier new]-v[/font][/color][/highlight] to catch the file names.
```
$ clamscan --max-filesize=3900M -r -v -i /
[...]
Scanning /usr/share/fwupd/uefi-capsule-ux.tar.xz
LibClamAV Warning: cli_scanxz: decompress file size exceeds limits - only scanning 103809024 bytes
[...]
```
And it seems that all the [highlight][color=black][font=courier]fmap_readpage: pread fail[/font][/color][/highlight]s and [highlight][color=black][font=courier]error[/font][/color][/highlight]s are from scanning /sys/

Need someone to tell me what's going on and what to do please. Hopefully that's enough info but if my post is missing details that will help you help me just say so and I'm on it. Thanks for any input

---

### Post by DuckHook on 2022-07-01
Welcome to the forums, norahlo.

The first issue I would raise is: why are you installing AV at all?

I'm a Linux power user who has been using various Linuxes since '95 and I've never found it necessary to install AV. Linux is different from the proprietary OSes in so many ways and one of the most pleasant is that it doesn't require the installation of AV.

Now, there are important caveats to this:

Rather than repeat myself, here's another post I wrote 9 years ago. Some of the info is a bit dated, but the general ideas are still perfectly valid: [https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795](https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795)

If I were you, I would uninstall the AV and stop stressing about it. I know this doesn't actually address your stated problem, but it's a meta&#8209;approach to the more fundamental issue.

---

### Post by norahlo on 2022-07-02
Thanks for your reply. I read your post. I agree that good security comes down to good habits more than anything. While I know that Linux viruses are unlikely, I figured an occasional scan doesn't hurt. Even if it seems like overkill, I'd rather just not have any Windows viruses sitting around, harmless though they may be.

I suppose AV is much less necessary right now; I'll consider moving on from ClamAV for the time being. But if I'm going to transfer files later on, or decide to install Windows alongside Ubuntu, I'd want to have it in place. (Right?) Also, I don't know if this is how it works, but, can things get left behind from Windows? 

Now that I've encountered issues I'd really rather just get to the bottom of them. Uninstalling would be easier for now, but if/when I reinstall it down the line, I'll be dealing with the same problem. I'd like to at least try to resolve it before uninstalling. If it proves too difficult, I'll still learn something. Those are just my thoughts, anyway. Am I being too stubborn? 

What are the chances that whatever's causing the issue will affect the functionality of other things? Could there be something wrong with the computer, or is it the AV? Maybe I messed something up at some point before or during the OS installation? Or ?

On a sidenote, is K. dated? Curious since I haven't heard of Links2.

---

### Post by DuckHook on 2022-07-02
> **norahlo said:**
> …if I'm going to transfer files later on, or decide to install Windows alongside Ubuntu, I'd want to have it in place. (Right?)
If you are worried about Windows malware, you need Windows&#8209;based solutions. Linux solutions will never be as complete or effective as solutions that are native  to Windows. Another reason why Linux AV is not only superfluous but may give a false sense of security.
> Also, I don't know if this is how it works, but, can things get left behind from Windows?
In theory, things can get left behind from Windows, but they are very exotic edge cases and I doubt that Clam would catch any of them. Purely as a theoretical exercise, I can imagine a piece of Windows malware that corrupts and stays resident in your UEFI or your HDD/SSD firmware. But how is Clam going to see such low&#8209;level malware? Clam isn't that sophisticated. If you get hit by stuff like that (highly unlikely BTW) Clam won't do any good anyway, so we are back to asking: "Why install it?"
> Now that I've encountered issues I'd really rather just get to the bottom of them. Uninstalling would be easier for now, but if/when I reinstall it down the line, I'll be dealing with the same problem. I'd like to at least try to resolve it before uninstalling. If it proves too difficult, I'll still learn something. Those are just my thoughts, anyway. Am I being too stubborn? 
I wouldn't call it stubbornness, but perhaps a misapprehension? In the proprietary universe from where you come, AV is a necessity. I wouldn't dream of running Windows without it. So, it is difficult for new users to get used to setting aside habits that have been drummed into them as "absolutely necessary". However, it is important to realize that you are changing an entire ecosystem. Sorta like moving to an Asian culture from a Western one and ridding oneself of the idea that knives and forks are "necessary" for good food etiquette in lieu of chopsticks.
> What are the chances that whatever's causing the issue will affect the functionality of other things? Could there be something wrong with the computer, or is it the AV? Maybe I messed something up at some point before or during the OS installation? Or ?
This is where I have to back out. I can't help you with Clam (or any AV for that matter). I don't use it, so I have no familiarity with it.
> On a sidenote, is K. dated? Curious since I haven't heard of Links2.
It isn't dated, but it may be overkill. When I wrote that advice, Firefox was a lot more loosey&#8209;goosey with their security and browsers like Brave did not exist. Modern browsers have better safeguards—provided that you stay away from Chrome. Links2 is available in the repos, but you won't like it. The reason it won't run scripts is because it is so primitive that it has no ability to do so. This same primitivism makes it an eyesore and an exercise in frustration for those used to modern browsers. You can always try it out by installing it with:```
sudo apt install links2
```…but I can almost guarantee that you will hate it. Make sure you invoke it with the -g flag to put it into graphics mode. Otherwise, believe it or not, it runs as a command line browser. How's that for primitive?

It really only makes sense for highly paranoid users like me. But even I use modern browsers for sites that will only work with scripting. However, I do find that Links2 is liberating when it comes to sites where I just want pure information and couldn't care less about the eye candy: example, news sites like The Economist. It has the fringe benefit of allowing me to bypass some paywalls too. Many paywalls are simply scripts that place an obscuring window over their content. A browser that is incapable of running scripts has the unintended benefit of not loading that obscuring window.

I still think that Clam AV is pointless, but if you are intent on using it, I hope another more knowledgeable member dives in here and can give you some direction.

Good Luck and Happy Ubuntu&#8209;ing!

---

### Post by #&amp;thj^% on 2022-07-08
Late for the party, but ClamAV, as all other antivirus software, can not scan a file that exceeds a certain volume. The message above just warns you that ClamAV has encountered a huge file and it can not scan it.
You can increase the scan size if your still interested:
Example:
```
sudo clamscan --max-filesize=30M -r -l ClamScanLog -i /
```
And I agree with DuckHook>>>"I still think that Clam AV is pointless"

---

