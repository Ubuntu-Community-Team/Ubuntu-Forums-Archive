---
title: "How to get rid of browser adware"
date: 2014-06-03
forum: Security
---

### Post by Sha'ir on 2014-06-03
I have the most oddest problem with Lubuntu 13.10. 
I have ad-ware on Chromium that keeps turning text into links to srv123.com(do not click on that link!). This site of course just redirects you to advertisements as expected. The issue though is that it is only on Chromium and Chrome but never on firefox.

So obviously I suspected it would be in a Chrome/Chromium folder which it is because every time I uninstall and purge every Google related folder it goes away for days on end until IT COMES BACK!(sort of like a M. Night Shyamalan movie after you think you couldn't possibly make another sucky film). I am essentially going through a constant cycle of uninstalling and re-installing Chromium and after a good 3 day wait the ad-ware will come back.

I have adware on windows OSs and had no issue sifting through extensions or out of place software but none of the basics are even working here. I cannot find any in Lubuntu that raises my eyebrow. I did not even know Lubuntu yet alone Linux distributions are susceptible to adware period.

Am I missing something?

---

### Post by monkeybrain20122 on 2014-06-03
Well you can still get adware through the browser in Linux if you visit dubious sites. The difference is that it is usually localized and easy to remove and it will not infect your whole system like in Windows. 

Reinstalling browser won't work because it is in your profile. In general reinstalling affects only system files (files in "File system" and in general need "sudo" to change) and it won't affect your user settings (in your /home). When you get adware through the browser it affects only you but not the system or other user accounts (if present, so e.g if you log into the guest account and start browser it would be ok), so the culprit is in your /home.

Close your browser. Open your file manager to your home directory. Press ctrl+h or choose show hidden files in the menu. Find the folder .config (note the ".", it is a hidden folder), get inside and if you use Chrome there is a sub-folder called google-chrome, just delete it and restart Chrome it should be fine.

I don't use Chromium but the procedure should be similar. If you can't find a chromium folder in .config it probably has it own folder in your home under the name of .chromium or .google-chromium.. Note the "." in front, it is always a hidden folder.

Edited: from this discussion it follows that next time if you want to visit dubious sites, it would be advisable to do it in guest session. Nothing stays on reboot. :)

---

### Post by cariboo on 2014-06-03
It might also help if you install a few addons, like Adblock+ and Disconnect

---

### Post by Sha'ir on 2014-06-03
> **monkeybrain20122 said:**
> Well you can still get adware through the browser in Linux if you visit dubious sites. The difference is that it is usually localized and easy to remove and it will not infect your whole system like in Windows. 

Reinstalling browser won't work because it is in your profile. In general reinstalling affects only system files (files in "File system" and in general need "sudo" to change) and it won't affect your user settings (in your /home). When you get adware through the browser it affects only you but not the system or other user accounts (if present, so e.g if you log into the guest account and start browser it would be ok), so the culprit is in your /home.

Close your browser. Open your file manager to your home directory. Press ctrl+h or choose show hidden files in the menu. Find the folder .config (note the ".", it is a hidden folder), get inside and if you use Chrome there is a sub-folder called google-chrome, just delete it and restart Chrome it should be fine.

I don't use Chromium but the procedure should be similar. If you can't find a chromium folder in .config it probably has it own folder in your home under the name of .chromium or .google-chromium.. Note the "." in front, it is always a hidden folder.

Edited: from this discussion it follows that next time if you want to visit dubious sites, it would be advisable to do it in guest session. Nothing stays on reboot. :)

I have been doing that this entire time :). I always deleted the config file after purging software. I even deleted the various libraries associated with Chromium that would not be deleted after purging. So when I say uninstall I mean uninstall EVERYTHING. Not a single byte is left from Chromium or Chrome unless I am missing something. Deleting the anything in the .config folder changes nothing which is why I am so baffled. I am fairly tech savvy and this is just mentally frustrating for me because I have removed rootkit viruses before(total pain) and for some simple adware to allude me is just embarrassing honestly :D.

Another issue though is that I use the Chromium browser for very routine stuff which is mainly forum posting. There has been no consistency with advertising also since I have adblock on and the advertisement banners on all sites have disappeared so I know I could not be getting adware through that old trick. I do not visit any dubious sites and I have just been using blogger, wikipedia and Google Drive for days straight drafting documents. 

Is 'Super Adware' a possibility here because I am all out of ideas  :).

---

### Post by Sha'ir on 2014-06-03
> **cariboo907 said:**
> It might also help if you install a few addons, like Adblock+ and Disconnect

Adblock does not help at all. Dealing with the Loki of the adware world here.

---

### Post by monkeybrain20122 on 2014-06-03
Hmm.. that is strange. If you removed chromium's config I can't see how it would still hijack your browser. How is Firefox working? 

 What if you create a test account? Is it affected?

---

### Post by Sha'ir on 2014-06-03
> **monkeybrain20122 said:**
> Hmm.. that is strange. What if you create a test account? Is it affected?

I have not created a test account yet. Considering that the adware is browser specific it never occurred to me to create a different userprofile. I will have to wait for the adware to comeback though because I just uninstalled Chromium last night. If the adware is like the Sand People it will come back(perhaps in greater numbers). Sort of hoping that is not the case though

---

### Post by Sha'ir on 2014-06-03
> **monkeybrain20122 said:**
> Hmm.. that is strange. If you removed chromium's config I can't see how it would still hijack your browser. How is Firefox working? 


Firefox is working like a charm but it does not have all of my bookmarks and useful apps/extensions that Chromium has. Only Google Chrome and Chromium are affected.

If I for example install Chrome while Chromium is infected the adware will appear on both Chrome and Chromium but never Firefox. Firefox has no extensions on it either such as adblock. If I uninstall Chromium completely(config files and all) and use Chrome for a few days the virus will pop up but on Chrome. Essentially this adware is a Google product only advertising generator

---

### Post by monkeybrain20122 on 2014-06-03
Did you clean your .cache? I find a subfolder called ~/.cache/google-chrome/

---

### Post by bapoumba on 2014-06-03
Please also have a look at your extensions and plugins and remove anything you do not recognize. Also ave a look at your sync, search and proxy settings.

---

### Post by monkeybrain20122 on 2014-06-03
Something may have attached to your google account/services. Not sure how but I am under the impression that Chrome (and probably Chromium too) integrates very tightly with a lot of google services and that's one reason why I use it only in a very limited way. I use Firefox for most things.

---

### Post by vasa1 on 2014-06-03
> **Sha'ir said:**
> I have not created a test account yet. Considering that the adware is browser specific it never occurred to me to create a different userprofile. I will have to wait for the adware to comeback though because I just uninstalled Chromium last night. If the adware is like the Sand People it will come back(perhaps in greater numbers). Sort of hoping that is not the case though

You're providing details that aren't helpful :)

What would be helpful is you sharing the list of sites you visit, whether you've synced your Google account, etc.

I find your thread title extremely unfortunate. There are quite a few users of Lubuntu who do not have the problems you're facing. Actually, your thread is the first I've come across implying that Lubuntu is associated in anyway with adware. Given the way search engines works, such titles can do more harm than good. It's really sad to see such a title.

---

### Post by sudodus on 2014-06-04
*vasa1* has a point. I modified the title to reflect the problem and hence a possible solution.

---

### Post by cariboo on 2014-06-04
Good call sudodus, I was just about to do the same thing, as the title was very misleading.

---

