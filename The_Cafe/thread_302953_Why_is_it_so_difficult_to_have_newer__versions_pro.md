---
title: "Why is it so difficult to have newer  versions programs in older Ubuntus?"
date: 2006-11-19
forum: The Cafe
---

### Post by Castar on 2006-11-19
Hi,

I'm using Dapper, but I would really like to have the version of Evolution coming with Edgy since it has the vertical pane which is much more usable on my widescreen screen. 

The problem is that from the repositories, there is no way to update Evolution. My only solution is to actually compile the newest Evolution version. I cannot install Edgy, as it has cpu-frequency issues and more importantly, I cannot run Tecplot which I really need. And before you ask, I need Evolution since my University uses an Exchange server for email, calendaring and so on.

So I pose my question: Why can't I not immediately install a newer version of a program for my linux which is only 5 months old? I mean, this is really a big drawback. In Windows, everyone can have the latest versions of all programs whenever they want. But if I want the latest Evolution, I have to compile it from source, which doesn't make so much sense. I understand the issue of stability and support but can't at least be a repository holding unsupported newest versions of the programs?

Am I unreasonable or not?

---

### Post by aysiu on 2006-11-19
You're not unreasonable. You're just used to a different software management model.

I think if people were used to Ubuntu's model, they would think the Windows model is unreasonable. Think about it. If people were used to upgrading their OS every six months and having that upgrade also upgrade all their installed applications at once, do you think they'd want the same OS for five years where they have to manually upgrade each package one at a time?

It's just a different approach.

---

### Post by Castar on 2006-11-19
I understand the model and it fits the perception that many people might have. But, what happens in the case that a newer version of a program (Evolution in this case) has a an essential feature for some? In this case, and I bet there are so many more, a vertical pane is important to me as I have a mini-laptop with a 12'' widescreen monitor. Having the email preview on the bottom of the  screen really makes it difficult for me to read my emails effectively. I am not saying that I cannot live without it, I am just wondering why I cannot easily upgrade.

For Kubuntu, you can install the newest KDE because J. Riddell is so great and he posts the compiled packages in a different separate repository. Why can't this be implemented for Gnome and its programs? I mean, having the choice (as in Windows) is liberty, when not it is a constraint.

---

### Post by aysiu on 2006-11-19
Upgrade to Edgy?

Or use Thunderbird, I guess. Thunderbird (even the older versions had it) has a vertical pane.

I don't know what else to tell you. Every operating system comes with its ups and downs. Ultimately, I like the Ubuntu model better, but one of the shortcomings is the ability to easily update application versions between releases.

You have a few options, of course, as I've mentioned:
1. Stick with the current version
2. Compile the latest version
3. Use another program (like Thunderbird)
4. Upgrade to Edgy

I think you know those four options already and that's why you're asking why it's so difficult. The literal answer is the shared libraries that are standard in Linux distributions. If every application brought its own set of dependencies and libraries (as they do in Windows), you could mix and match versions.

---

### Post by Castar on 2006-11-19
Yes, these options make sense. I can only really do 1 or 2, as I cannot use Thunderbird  as I need the Exchange capabilities of Evolution and Edgy cannot run the propriety program I need (Tecplot), as I get libc.so.6 errors from it.

Unfortunately, my University has a Microsoft campus agreement :???: which makes all MS programs the defaults... I will not dump Ubuntu for this of course, as there are alternative options. As another example, what is the point of not-having Firefox 2.0 in Dapper and to have to search through the wikis to learn how to compile it and circumvent the default Dapper package? I am not complaining, as I can do it myself. I am just arguing the case for the creation of a separate repository (not enabled by default) that will have newer versions of programs.

---

### Post by John.Michael.Kane on 2006-11-19
Have a read [http://ubuntuforums.org/showthread.php?t=269238](http://ubuntuforums.org/showthread.php?t=269238)

You can also try asking for certain programs to be backported [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47). note not every edgy program can be backported.

---

### Post by kuja on 2006-11-19
Actually, said repository already exists. The backports repository. 

AFAIK the reason many apps aren't backported is because you would have to backport many or all of the libraries they depend on as well.

Edit: Oh, SD Plissken beat me to it.... oh well.

---

### Post by Castar on 2006-11-19
Thanks, you have been very helpful. The above information doesn't solve my problem, but at least I know that I can at least put some newer versions in the backports server.

In the end, it all boils down to the Ubuntu philosophy ;)

But I still think that some programs are very important to be kept in their older versions, like Firefox.

---

