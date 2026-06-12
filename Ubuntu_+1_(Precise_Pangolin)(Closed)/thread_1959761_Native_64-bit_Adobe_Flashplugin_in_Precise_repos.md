---
title: "Native 64-bit Adobe Flashplugin in Precise repos"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-04-16
For the people who have manually downloaded and installed the 64-bit libflashplayer.so, shared object, from Adobe site, now there is a right choice to do this.
You can install the adobe-flashplugin (11.2.202.233-0precise1) package from Precise repos.
You just have to enable partner repos.
This is the native 64-bit plugin.

---

### Post by zika on 2012-04-16
> **Harry33 said:**
> For the people who have manually downloaded and installed the 64-bit libflashplayer.so, shared object, from Adobe site, now there is a right choice to do this.
You can install the adobe-flashplugin (11.2.202.233-0precise1) package from Precise repos.
You just have to enable partner repos.
This is the native 64-bit plugin.Especially now bearing in mind that it is also the last ... ;)

---

### Post by t1497f35 on 2012-04-16
> **zika said:**
> Especially now bearing in mind that it is also the last ... ;)
It's the last one not for Linux, but for the Linux browsers which don't implement the new pepper plugin API, so it's the last one for the likes of Firefox, not for Chrome.

---

### Post by zika on 2012-04-16
> **t1497f35 said:**
> It's the last one not for Linux, but for the Linux browsers which don't implement the new pepper plugin API, so it's the last one for the likes of Firefox, not for Chrome.I think they come in another package. I might be (as many times before) wrong... ;)

---

### Post by t1497f35 on 2012-04-16
> **zika said:**
> I think they come in another package. I might be (as many times before) wrong... ;)
They who? I'm not sure I get you. Chrome comes bundled with flash and when a new version of flash comes out Google updates Chrome and ships as an update.

To me the real problem is that I don't wanna switch to Chrome since from my experience none of its ad-block extensions are nearly as good as Firefox's one. It's a show-stopper for me.

---

### Post by zika on 2012-04-16
> **Harry33 said:**
> For the people who have manually downloaded and  installed the 64-bit libflashplayer.so, shared object, from Adobe site,  now there is a right choice to do this.
You can install the adobe-flashplugin (11.2.202.233-0precise1) package from Precise repos.
You just have to enable partner repos.
This is the native 64-bit plugin.> **zika said:**
> Especially now bearing in mind that it is also the last ... :wink:> **t1497f35 said:**
> It's the last one not for Linux, but for the Linux browsers which don't implement the new pepper plugin API, so it's the last one for the likes of Firefox, not for Chrome.
> **zika said:**
> I think they come in another package. I might be (as many times before) wrong... :wink:
> **t1497f35 said:**
> **They who? I'm not sure I get you. **Chrome comes bundled with flash and when a new version of flash comes out Google updates Chrome and ships as an update.
To me the real problem is that I don't wanna switch to Chrome since from my experience none of its ad-block extensions are nearly as good as Firefox's one. It's a show-stopper for me.
To be precise (pun intended): OP stated that there is a package to install Adobe Flash pligin on 64-bit machines (a.k.a. 11.2.202.233-0precise1). I said that it is (likely) a last one since (I do expand my sentence now) (as You said) &#8222;it's the last one for the likes of Firefox, not for Chrome&#8220;... I responded that flash plugin in those other browsers come in other package(s) which You (as a matter of fact) did support with: &#8222;Chrome comes bundled with flash and when a new version of flash comes out Google updates Chrome and ships as an update.&#8220;... Ergo: package  adobe-flashplugin is... see above... ;)

---

### Post by dino99 on 2012-04-16
Lightspark is a free Flash player for Linux which aims for high-performance
by using modern technologies such as JIT compilation and OpenGL shaders.

---

### Post by zika on 2012-04-16
> **dino99 said:**
> Lightspark is a free Flash player for Linux which aims for high-performance
by using modern technologies such as JIT compilation and OpenGL shaders.Where it is better than Adobe and what are weaknesses?

---

### Post by lovinglinux on 2012-04-16
The 64bit package has been available from the Partner repos from some time, is not new. Even the *flashplugin-installer* from official repos already install the real 64bit version.

This version is a minor update, that fixes security issues. It doesn't solve recent problems, like SMURF effect, caused to nVidia users. 

This is not the last version Adobe will release. They will continue to release minor version updates like this for 5 years, to address security issues, but they won't fix bugs or release major versions with new features. Flash on Linux will always remain as 11.2.xxx.yyy, while on Windows is heading to 11.3.xxx.yyy.

BTW, I was never able to make Lightspark work and Gnash on works on YouTube, not on any other site I use.

---

### Post by t1497f35 on 2012-04-16
> **zika said:**
> Where it is better than Adobe and what are weaknesses?
Don't bother trying out lightspark. While I respect the devs ideas, none of the available flash alternatives works well enough, they often work bad or not at all.

---

### Post by ubuntu27 on 2012-04-16
Currently [Lightspark]("http://lightspark.github.com/") is in **Alpha **development stage. It says so in the package description in Synaptic Package Manager.

One is free to test them of course :popcorn:

---

### Post by xebian on 2012-04-16
> **t1497f35 said:**
> They who? I'm not sure I get you. Chrome comes bundled with flash and when a new version of flash comes out Google updates Chrome and ships as an update.

To me the real problem is that I don't wanna switch to Chrome since from my experience none of its ad-block extensions are nearly as good as Firefox's one. It's a show-stopper for me.

Only the Google Chrome 32-bit has the Adobe flash bundled.

The 64-bit stable and beta does not.  The 64-bit dev has the pepper flash.

---

### Post by Starks on 2012-04-16
What about Chromium?

Also, is the Pepper Flash binary going to be baked in or its own file available for reverse engineering?

---

### Post by xebian on 2012-04-16
> **Starks said:**
> What about Chromium?

Also, is the Pepper Flash binary going to be baked in or its own file available for reverse engineering?

I'm guessing if you are using the dev trunk for chromium then it's there in the PepperFlash directory.  Not sure about chromium from the repo but the Google chrome is installed in /opt/google/chrome.

It's a module/plugin loaded on demand.

---

### Post by lovinglinux on 2012-04-16
> **Starks said:**
> What about Chromium?

Also, is the Pepper Flash binary going to be baked in or its own file available for reverse engineering?

Most likely it will not have PepperFlash, just like it doesn't have the bundled flash now.

---

### Post by xyzzyman on 2012-04-16
This new 11.2 build does seem to fix the blue smurfs effect even with hardware acceleration turned on...

EDIT: I apparently lied... :(

---

### Post by jbicha on 2012-04-16
> **Starks said:**
> What about Chromium?

Also, is the Pepper Flash binary going to be baked in or its own file available for reverse engineering?

Flash is proprietary and closed source; Ubuntu's Chromium can't and won't bundle it.

---

### Post by zika on 2012-04-18
I could not resist and embrace the opportunity to install (after years of doing that manually via cp) this package. Thank You... ;)
Update&#8321;: If I install adobe-flashplugin & adobe-flash-properties-gtk it does not work if I do not (as always) manually copy libflashplayer.so to (for example) ~/.mozilla/plugins. So, essentialy it is not working... It installed in /usr/lib/adobe-flashplugin/libflashplayer.so
             If I install flashplugin-installer it works out of the box... ;) It installed in /usr/lib/flashplugin-installer/libflashplayer.so

---

