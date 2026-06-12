---
title: "[SOLVED] Firefox and extensions like Adobe etc."
date: 2007-07-10
forum: Ubuntuzilla
---

### Post by ingridt on 2007-07-10
Used the ubuntuzilla-script to install the lastest Firefox on my recently installed kubuntu 6.06. It works, but many sites require things like Adobe Flash player, Realplayer, Java Runtime Environment. 

the  "click here to download the plug-in" does not work.:confused:

Also this Firefox does not (yet) open pdf-documents.I'll make a different post, as I think this is another thing.

I did install add-ons like del.icio.us an fireFTP without any difficulty - coming straight from mozilla.

My question: where do I find the instructions to make this Firefox complete so all websites can be used if they require special extensions that are not coming from Mozilla?

---

### Post by nanotube on 2007-07-10
for embedded videos, install package "mozilla-mplayer"
for jre, i don't recall what the packages were on 6.06, but there should be something like java-plugin (search for "java" or "plugin" in synaptic)

for flash, get the latest flashplayer from adobe (v9.0.31), unzip, and put the files into the /opt/firefox/plugins directory.

about pdf: i will reply to your other thread. :)

---

### Post by ingridt on 2007-07-11
I search in adept for java and find that already quite some of these are installed; one of them called java-gcj-compat (java runtime environment using GIJ)

Still the bank website/firefox tells me it needs Java runtime environment

Possibly it was not installed correctly? I've had quite some problems installing something for firefox before I found and  decided to move on to ubutuzilla. I had to accept some license, but I had no key to how to tell the system I accepted (adept kept on waiting, and there was no screen nor button to give a YES), so funny things happened and I tried many things which I cannot reconstruct.

So this one is not yet solved.

---

### Post by ingridt on 2007-07-11
adept does not want to install mozilla mplayer as it would BREAK other packages, it says.

But I see there are other mplayers installed and I try these. They do not work either, but as this is with Konqueror I put a new question on the appropriate forum.

---

### Post by nanotube on 2007-07-12
> **ingridt said:**
> adept does not want to install mozilla mplayer as it would BREAK other packages, it says.

But I see there are other mplayers installed and I try these. They do not work either, but as this is with Konqueror I put a new question on the appropriate forum.

what packages does it say would break?

and about java, look for one that has "plugin" or "mozilla" in the name, if you want to get the browser plugin. java-gcj is an "alternative" java implementation, and should work just as well, but you have to have the plugin as well.
i just looked on my comp (feisty), the gcj plugin package is called "java-gcj-compat-plugin". try that one?

---

### Post by ingridt on 2007-07-13
> **nanotube said:**
> 
for flash, get the latest flashplayer from adobe (v9.0.31), unzip, and put the files into the /opt/firefox/plugins directory.


I miss some information on what exactly to do.
I downloaded and unpacked into the default extract-directory.
first dead-lock: follow adobe instruction of typing ./flashplayer-installer, but as I am not  root   it made an installation in /home/ingrid/.mozilla > moving this file to /opt/firefox/plugins has no effect.

second dead-lock: moved all extracted files into /opt/firefox/plugins and typed sudo ./flashplayer-installer
Now it asks for the installation path of firefox etc; answering /usr/bin/ gives a "please give a valid installation path"

:mad::(

Isn't this a problem every user has to solve? isn't there a step-by-step procedure to follow? (all other things in this thread are still giving me headaches, too)

---

### Post by ingridt on 2007-07-13
adept does not say which packages would break when installing mozilla-mplayer, not at request for install and not at attempt to install: it refuses to install, saying packages will break.

---

### Post by ingridt on 2007-07-13
> and about java, look for one that has "plugin" or "mozilla" in the name, if you want to get the browser plugin. java-gcj is an "alternative" java implementation, and should work just as well, but you have to have the plugin as well.
i just looked on my comp (feisty), the gcj plugin package is called "java-gcj-compat-plugin". try that one?

There is java-gcj-compat and java-gcj-compat-dev, but nothing with java and plugin exept something for Gnome MonoDevelop.
mozilla plugin does not give anything with java either.
 Would it all be ready to go in another version of kubuntu?

---

### Post by nanotube on 2007-07-13
> **ingridt said:**
> There is java-gcj-compat and java-gcj-compat-dev, but nothing with java and plugin exept something for Gnome MonoDevelop.
mozilla plugin does not give anything with java either.
 Would it all be ready to go in another version of kubuntu?

well, it should be all there in feisty 7.04, if that's what you're asking. :) in feisty there's even official sun java, and sun java plugin in the repositories, and mozilla-mplayer is there too (though that used to work for me on dapper as well...).

but if you're not up to an upgrade, you could ask around elsewhere on the forum, maybe someone will be able to help you out with this plugin stuff...

---

