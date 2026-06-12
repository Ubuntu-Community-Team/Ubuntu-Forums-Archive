---
title: "Not showing the right ammount of threads (Linux NOOB)"
date: 2023-12-15
forum: Virtualisation
---

### Post by meldiuz on 2023-12-15
Hello there just moved over from windows to linux and would like to get going on virtualization, but wen following a guide i got stuck on a problem. 

the problem is that wen doing 

                       [LEFT] egrep -c '(VMX|SVM)' /proc/cpuinfo 

i got 0 , which makes no sense because i have a AMD Ryzen™ 9 3900X × 24  

and virtualization is enabled and i have checked with 

                        lscpu

and under were it says Virtualization feature it says AMD-V so at least from my understanding that means its enabled and i have also prior to doing that check made sure that its enabled in bios as well. 

so im just trying to get some hints on were to start looking so i can solved the problem. thanks in advance  :P


[/LEFT]

---

### Post by #&amp;thj^% on 2023-12-15
What guide are you following? we need to know to help.
Mine shows the same as you see, but please look here:
```
lsmod | grep kvm
kvm_amd               208896  0
kvm                  1404928  1 kvm_amd
irqbypass              12288  1 kvm
ccp                   135168  1 kvm_amd

```
You must be following an old how to.

---

### Post by meldiuz on 2023-12-15
i see you also get 0 there so im guessing its not that important ? 


The guide i'm trying to follow right now is [https://www.youtube.com/watch?v=4m6eHhPypWI](https://www.youtube.com/watch?v=4m6eHhPypWI) and its 3 months old.

---

### Post by #&amp;thj^% on 2023-12-15
> **meldiuz said:**
> 
The guide i'm trying to follow right now is [https://www.youtube.com/watch?v=4m6eHhPypWI](https://www.youtube.com/watch?v=4m6eHhPypWI) and its 3 months old.

Pretty much spot on for starters.
Commands
```
sudo apt update
sudo apt install qemu libvirt-daemon-system libvirt-clients bridge-utils virt-manager ovmf

```
// Enable QEMU/KVM
```
sudo systemctl enable libvirtd
sudo systemctl start libvirtd

```
// Add users to libvirt Group
```
sudo useradd -g $USER libvirt
sudo useradd -g $USER libvirt-kvm

```
And just to check
```
groups
me adm cdrom sudo dip plugdev users lpadmin sambashare docker libvirt

```
Have fun.

---

### Post by MAFoElffen on 2023-12-15
> **meldiuz said:**
> 
the problem is that wen doing 
```

                       [LEFT] egrep -c '(VMX|SVM)' /proc/cpuinfo 
[/LEFT]

```[LEFT]
[/LEFT]
[LEFT]
[/LEFT]
 It gave you the correct answer for what you asked...


Try it as either 
```

grep -i -c 'VMX\|SVM' /proc/cpuinfo
# or
grep -c 'vmx\|svm' /proc/cpuinfo

```
Hint, case and syntax error in your match pattern...

1fallen is correct, in that you must have been using an old guide somewhere. egrep has been degraded and discouraged for years now. (In favor, lean to just grep)

---

### Post by #&amp;thj^% on 2023-12-15
> **MAFoElffen said:**
> [LEFT]
[/LEFT]
 It gave you the correct answer for what you asked...


Try it as either 
```

grep -i -c 'VMX\|SVM' /proc/cpuinfo
# or
grep -c 'vmx\|svm' /proc/cpuinfo

```
Hint, case and syntax error in your match pattern...

1fallen is correct, in that you must have been using an old guide somewhere. egrep has been degraded and discouraged for years now. (In favor, lean to just grep)
+1
ie:
```
 grep -i -c 'VMX\|SVM' /proc/cpuinfo
12

```
I should have wrote that though for someone new-ish to Buntu
Thanks MAFoElffen ;)

---

### Post by meldiuz on 2023-12-16
[ 						 							]("https://ubuntuforums.org/member.php?u=1044547")Thx allot for the answers both of you <3 , i will get to testing it as soon as i have the opportunity :D , have a nice day ^^

---

### Post by TheFu on 2023-12-16
$ egrep -ci '(VMX|SVM)' /proc/cpuinfo

grep and egrep are different.  I don't think grep supports the enhanced regex used.
```
$ **egrep **-ci '(VMX|SVM)' /proc/cpuinfo 
12

$ **grep** -ci '(VMX|SVM)' /proc/cpuinfo 
0

```
Being case-insensitive is important.  You can always just look at the file contents ... 
```
$ less /proc/cpuinfo 
```
to see what's wrong with a regex.  

Also, grep != egrep unless you add the -E (enhanced) option.
```
$ **grep** -Eci '(VMX|SVM)' /proc/cpuinfo 
12
```

Yep, that works.  I'm lazy and don't like wasting an extra 2 characters in a command, so I use **egrep** even though it has been listed as deprecated.  When that happens, I have hundreds of scripts that will need to be fixed.

---

### Post by The Cog on 2023-12-16
That has me confused.
```
~$ grep -c 'vmx|svm' /proc/cpuinfo
0
~$ egrep -c 'vmx|svm' /proc/cpuinfo
8
```
I always assumed that meant "this word or that word" was only in the extended grep. So seeing this confuses me:
```
~$ grep -c 'vmx\|svm' /proc/cpuinfo
8

```
I didn't think that was possible, and have always used egrep for OR-ing words. What is the backslash doing - why is it needed in grep but not egrep?

---

### Post by #&amp;thj^% on 2023-12-16
Seems it needs an escape for that command, I wondered my self after TheFu and you commented.
 MAFoElffen can give his reason for it.

---

### Post by MAFoElffen on 2023-12-16
Difference between the -E and -e flags... and how they process REGEX patterns differently between the two.

@TheFu -- "You are that person" who spend a lot of effort to convince me to stop using 'egrep', and why. I used to use it a lot, in the past... Until you made your arguments to me about that, to convince me. LOL. Are you going back on that now?

---

### Post by TheFu on 2023-12-16
> **MAFoElffen said:**
> @TheFu -- "You are that person" who spend a lot of effort to convince me to stop using 'egrep', and why. I used to use it a lot, in the past... Until you made your arguments to me about that, to convince me. LOL. Are you going back on that now?

Don't think that was me. egrep is deprecated.  I use it. I like readable code, but also like to save a character for commonly used commands.  I use **egrep** 99.999999% of the time, so I don't have to think about whether extended regex is supported or not. Just a habit for my fingers at this point.  If egrep disappears, I'll make an alias for CLI use and will probably change my command at the top of every script from 
```
EGREP='/usr/bin/egrep' 
```to 
```
EGREP='/usr/bin/grep -E' 
```
Glad I have that habit.

**grep** and **egrep** use different regex engines.

sed and perl have different regex engines.  sed is very limited IME and I often get into trouble because it doesn't behave in the way I'm used to, so I don't really use sed for anything non-trivial; instead I use perl, which has the most awesome regex capability ... which includes the ability to fully comment the regex so it is documented as created.  Mastering Perl by Brian Foy has a chapter about regex and commenting.  Changed my life.  He visited our Perl group ... then signed everyone's copy of his book.

I think the () are superfluous in egrep for the example above.
I have doubts that the grep example with the \| actually does what we think, due to the single-quoting.

---

### Post by #&amp;thj^% on 2023-12-16
Note however that while egrep and fgrep are deprecated, they're almost certainly not going away any time soon. A quick scan of scripts in /usr on my laptop (which is running Gentoo/Arch/FreeBSD Linux) finds a few dozen software packages that have scripts which use one or the other, including such ubiquitous things as Python and GCC.

Given all this, one can rather ironically conclude that code that uses the deprecated commands instead of the options is actually more portable than code which uses the options, since it will run on older systems that code using the options won't.
EDIT: Forgot the link: [https://github.com/rhimmelbauer/egrep/issues/1](https://github.com/rhimmelbauer/egrep/issues/1)
Replacing egrep with grep -E would remove the above limitation. We can
expect future linux releases to remove egrep (as well as fgrep).

---

### Post by MAFoElffen on 2023-12-16
> **TheFu said:**
> Don't think that was me. [COLOR=#ff0000]egrep is deprecated.[/COLOR]  I use it. 
That is exactly what you told me, and the why you said for me to stop using it... So I did. About 2 years ago. I listened to you, and conceded to what you told me, as it being good advice. LOL!!!

---

### Post by #&amp;thj^% on 2023-12-16
@ meldiuz  Sorry for all the posts, if you want us to, we could split this portion of your thread to the jail or another Chat Area.
there is some good information here though, albeit not about your original topic though.
Regards

---

### Post by MAFoElffen on 2023-12-16
LOL. Good education. There are 100's of ways to do the same things in Linux. 

Curious to see how his KVM install goes.

---

### Post by TheFu on 2023-12-16
LVM? I must have missed that detail.

---

### Post by MAFoElffen on 2023-12-16
(*KVM... Typo)

---

### Post by meldiuz on 2023-12-17
well you learn something new everyday i will only try to use grep from now on :)

---

### Post by TheFu on 2023-12-17
> **meldiuz said:**
> well you learn something new everyday i will only try to use grep from now on :)

NOOOOO!  Use **egrep**! ... and remember that at some point, you may need to use **grep -E** for exactly the same behavior.

The manpage says this:
```

       In addition, the variant programs egrep, fgrep and rgrep are the same as  grep -E,  grep -F,
       and  grep -r,  respectively.   **These  variants are deprecated**, but are provided for backward
       compatibility.
```

Save the '{space}-E{space}' with just 'e'. Be more efficient. ;)  Screw their deprecation. Next _they'll_ try to take away X/Windows or xinit.  That won't get _them_ far. We'll show _them._

---

