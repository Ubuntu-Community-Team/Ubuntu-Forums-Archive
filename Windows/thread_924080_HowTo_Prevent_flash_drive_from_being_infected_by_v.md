---
title: "HowTo: Prevent flash drive from being infected by virus"
date: 2008-09-19
forum: Windows
---

### Post by lian1238 on 2008-09-19
This short tutorial is intended mostly for Windows users, but users of other OS's can also use this technique to keep your flash drives safe.
[B]
How?
[/B]It's simple! Create a **folder** named "autorun.inf" in your flash drive or external harddisk. That's IT!

This technique can prevent auto-running viruses from spreading through your flashdrive or external HDD, aka hitch-hiking.

Note that if your flash drive is already infected or if there's already a file named "autorun.inf" you cannot create the folder. You'll have to find a way to delete that file first.

If you can't see the hidden autorun.inf file, you need to show hidden files then delete it.
To unhide hidden files and folders:
1. Open My Computer (or any folder)
2. Go to tools->folder options
3. Go to the View tab
4. Check/tick: "Show hidden files and folders"
[I] If there is no Folder Options under Tools, and you are sure you have administrative rights, you're probably infected with a virus which hides that menu option (and ALL the hidden files). Uh oh. Don't hide any important files because you won't be able to find them later! Find a way to kill that virus, and quick!
[/I] 
[B]How does this method work?
[/B]As you might already know, viruses often create a file called autorun.inf in your external drive so that it can copy itself upon being inserted into a Windows machine. Windows will automatically run the little script, whether it's an automated installation setup.. or a virus! Therefore, if there's already a folder with that name, a file with the same name cannot be created, effectively disabling the virus to autorun itself.

**To reverse this**, simply delete the folder you created, "autorun.inf".

---

### Post by Ptero-4 on 2008-09-28
To delete the virus just use the tools you already got (a.k.a your linux distro). How, simple. Open the infected pendrive while you´re on linux and delete the autorun.inf and recycler and/or restore folder´s (those are the two more common ones the pendrive viruses use to hide in) and then put the autorun.inf folder/file. You can also disinfect a wintendo box that caught any one of those two viruses by booting it off a linux LiveCD and doing the deletion procedure as it would be done for a pendrive.

---

### Post by lian1238 on 2008-09-28
You can't guarantee you'll be able find the virus even from your linux. Disinfecting a USB drive from linux is easy as pie - just delete those folders you mentioned. But to disinfect an infected Windows is a different story. Granted, it'll be easier if you used Linux to delete the virus(es) since the infection is not in effect, therefore not hiding anything.

Another approach is to boot into safe mode in Windows and go from there. You'll be able to edit registry keys if you need to.

---

### Post by Liviu-Theodor on 2008-10-29
I had a case, which gave me a virus (from an original CD, to install the software for an UPS) that manifested itself like a process named "kill" in the Task Manager and two files in the "root" of each partition or removable drive. One of it is called "autorun.inf". I think that one should apply your suggestion also on hard disks, to prevent also spreading a non-removable disk. That is because also on such drives Windows will try to run what is on the "autorun.inf" file.

---

### Post by lian1238 on 2008-10-29
> **Liviu-Theodor said:**
> I had a case, which gave me a virus (from an original CD, to install the software for an UPS) that manifested itself like a process named "kill" in the Task Manager and two files in the "root" of each partition or removable drive. One of it is called "autorun.inf". I think that one should apply your suggestion also on hard disks, to prevent also spreading a non-removable disk. That is because also on such drives Windows will try to run what is on the "autorun.inf" file.

Are you certain it is a virus? I'm saying, it could be a software to automatically shutdown your computer when your UPS is out of battery. It's unlikely for an original CD to install a virus on your computer. By the way, did you know what the software was for? It's strange for an UPS to need a software.

---

### Post by Liviu-Theodor on 2008-10-30
> **lian1238 said:**
> Are you certain it is a virus? I'm saying, it could be a software to automatically shutdown your computer when your UPS is out of battery. It's unlikely for an original CD to install a virus on your computer. By the way, did you know what the software was for? It's strange for an UPS to need a software.

I am sure, because the files and the processes persisted to be there even after uninstalling the software, and antivirus programs also said so. And the UPS works just fine also without software, which was supposedly used for monitoring the waveform of the input (maybe also output?) voltage, like an oscilloscope. And because the files just copyed themselves to any disk they could. And I (and others I know) found out viruses on many original CD's (verifyed with antivirus programs), even so many I can not even trust anymore using even original (non-free and non-open-source) software. One good reason to stick to free and open source software (not the only one), isn't it (or at least trying to)?

---

### Post by Thelasko on 2008-10-30
> **lian1238 said:**
> Note that if your flash drive is already infected or if there's already a file named "autorun.inf" you cannot create the folder. You'll have to find a way to delete that file first.

That's interesting, I figured a virus would simply overwrite a preexisting autorun.inf file.

Wouldn't it be easier to disable autorun on your machine?

---

### Post by Liviu-Theodor on 2008-10-31
> **Thelasko said:**
> That's interesting, I figured a virus would simply overwrite a preexisting autorun.inf file.

Wouldn't it be easier to disable autorun on your machine?

Yes, this can be a solution, if the virus programmer does not think about it (and of course, the virus can spread itself even with the autorun feature off).

---

### Post by lian1238 on 2008-11-02
> **Liviu-Theodor said:**
> Yes, this can be a solution, if the virus programmer does not think about it (and of course, the virus can spread itself even with the autorun feature off).
Yes, that stops the virus from infecting your computer (automatically) on insertion. But you can double-click the flash drive and still get infected (correct me if I'm wrong). If you have an autorun.inf folder on your flash-drive, you refuse to let viruses hitch-hike on your USB drive. Protecting your computer from viruses is a different story. You can get something like **autorun killer**. Someone told me **avast!** anti-virus scans and kills viruses on flash drive and prevents autorun-virus infections. I haven't tested this myself.

---

