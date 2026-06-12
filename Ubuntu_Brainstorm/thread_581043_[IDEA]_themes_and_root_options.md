---
title: "[IDEA] themes and root options"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by manoswerts on 2007-10-19
Hi,

I think that there still can be an improvement in the standard themes that Ubuntu provides.

In Hardy Heron I like to see a darker theme (not everything dark like a lot of themes on the net but like Windows Vista for example) and a theme that resembles more to the colors used in Mac OS  X (light grey and a nice blue). With these new themes i like to see a restylment of the minimize, maximize and close buttons. The squares around these buttons are (in my opinion) ugly. Just getting rid of them and leave only the icons the contain would be a very big improvement on itself.

Also the icons used are (in my opinion again) ugly. Standard there should be on option to choose more stylish icons like icons that resemble to the nice design look and feel of Mac OS X or Windows.
I know that lot of linux users prefer simplistic icons, but I think that there are also a lot of people thinking the same way I do.
And sure I know that I can download a lot of icon packs, but most of them aren't complete (doesn't change trash can, network manager, sound icon, battery icon, etc).


My second idea relates to the option of logging in as root. It is a real pain in the *** (forgive my words) sometimes that you got to log out and then login as root to do some changes. I'd like to see an implementation like in Fedora, where you just can temporarirly login as root from your account in graphical mode to do a couple of things. This would be a lot easier for beginning linux users, and I think it is one of the biggest objectives of Ubuntu to make it accessible and easy for everyone.

I hope my ideas will be reconsidered and implemented.
The only thing I just like to say is that everybody of the Ubuntu developing theme did a good job!!

Friendly regards,

Mano

---

### Post by Zdravko on 2007-10-19
First idea: bad, since I don't care for fancy graphics but usability and stability.
Second idea - why would I ever need to log in as a root?

---

### Post by bethaviv on 2007-10-19
> **Zdravko said:**
> First idea: bad, since I don't care for fancy graphics but usability and stability.

Maybe you don't but others do.

> **Zdravko said:**
> Second idea - why would I ever need to log in as a root?

Maybe you don't but others do.

---

### Post by Zdravko on 2007-10-19
Ah, yes - you are damn right. I am too solemn now.

---

### Post by Twintop on 2007-10-19
> **manoswerts said:**
> 
My second idea relates to the option of logging in as root. It is a real pain in the *** (forgive my words) sometimes that you got to log out and then login as root to do some changes. I'd like to see an implementation like in Fedora, where you just can temporarirly login as root from your account in graphical mode to do a couple of things. This would be a lot easier for beginning linux users, and I think it is one of the biggest objectives of Ubuntu to make it accessible and easy for everyone.


There's a way to do this:
```
#sudo su
```But it is not recommended, again, because of security and lack of sanity checks. It's one thing to run command as your own user where you're limited in what you can do, and have to specify that you want to run a command as root to get a task done. Giving a new user free reign over their system as root might have some good aspects as a teaching tool, but should not be needed or used; there are other methods that work just as well.

---

### Post by aysiu on 2007-10-19
> **manoswerts said:**
> 
My second idea relates to the option of logging in as root. It is a real pain in the *** (forgive my words) sometimes that you got to log out and then login as root to do some changes. I've *never* had to log in as root to do some changes in Ubuntu.

Name a change in Ubuntu that necessitates logging out of user and separately logging in as root.

---

### Post by Zdravko on 2007-10-19
There is no such change.

---

### Post by manoswerts on 2007-10-22
I got an example..

If you install LAMP you have to  put your files in /var/www and believe me, try that without changing the permissions. Quanta can't save its projects in it because it isn't available. So it would be handy for people that don't like to use the command line that they can access them as root in a graphical user interface.
And i think there are a lot of situations, otherwise Fedora wouldn't have implemented the feature...

@Zdravko : you have said it in a lot of threads that you don't like fancy graphics, and i think everybody knows your opinion about now.. i don't think that giving others the oportunity to select a fancy theme will do you any harm..

---

### Post by DizzyTech on 2007-10-22
It would either take some time to fix from the command line (using chmod and chown).  You could also run either "gksudo nautilus" to fix the permissions, or "gksudo quanta" to run the program as root.

---

### Post by bikeboy on 2007-10-23
Or ```
sudo cp /directory/with/webfiles /var/www
```

---

### Post by exile on 2007-10-23
I haven't tried this with Gutsy but it used to work pre-Feisty.

You could just enable the root account and then fast user switch to the root account?

Now personally I'd never do this. As far as I'm concerned if you have to develop webpages with root privs then something has gone wrong. I create a webdev group and grant read/write perms for the directory. Maybe there is a better way than this.. maybe my suggestion isn't very safe either, but I believe in doing as little as possible as root.

---

### Post by luisjorge on 2007-10-23
Hi!

Regarding the first idea in the first post, I agree that maybe the default themes that Ubuntu comes with could be more stylish, but always following the "feel" and look of Ubuntu. Why include with Ubuntu a theme so like Mac OS? Both are separate, different OS, and yes, Mac looks really cool, simple (sometimes) and clean, but I think that could be achieved without losing the original Ubuntu look idea (like the colors, for example).

As to the second idea, I don't think it's a veeery good idea. Yes, there are certain things that you need to be root to do them properly, but I'm happy with the terminal for that. I don't have to log out, and being really honest, it's not that hard. Just type sudo, or su or su -, depending on what you want to do, type your password and that's it! Of course, there's always the graphical root option, with the "gksudo nautilus" command, that you can run with Alt+F2.
Also, imagine this: someone (or yourself) are working in your computer. You log in as root, because you have to do some changes. You have to go somewhere and leave it there for some moments. Then someone approaches and, if you didn't lock the screen, or the screensaver hasn't activated, or isn't locked, then he or she has complete access to your files, configuration, system...in other words, that person can completely screw up your system in a few moments, and wouldn't be asked for a password ever by the computer. That doesn't sound very secure to me, plus that is more or less (very simplified) what happens with viruses and other attacks, which is a problem present in Windows.

---

