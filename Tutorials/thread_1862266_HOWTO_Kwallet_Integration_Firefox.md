---
title: "HOWTO: Kwallet Integration Firefox"
date: 2011-10-16
forum: Tutorials
---

### Post by HalfEmptyHero on 2011-10-16
GuillermoMolina has a Firefox extension allowing integration with kwallet, however it is not as simple to setup as most extensions so I figured I would write a tutorial on how I got it to work. This tutorial is for Kubuntu 11.10/Firefox 7.0.1 so you may have to tweak it if you aren't using both of those.

Since Oneiric doesn't have xulrunner in the repos, the first thing you need to do is install it.

Download:
If you are using 32-bit Kubuntu:

```
wget http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/7.0.1/runtimes/xulrunner-7.0.1.en-US.linux-i686.tar.bz2
```If you are using 64-bit Kubuntu

```
wget  http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/7.0.1/runtimes/xulrunner-7.0.1.en-US.linux-x86_64.tar.bz2
```The rest of the install is the same:

```
tar xvjf xulrunner-7.01.en-US.linux*.tar.bz2
sudo cp -r xulrunner /usr/local/lib/xulrunner-7.0.1
sudo ln -s /usr/local/lib/xulrunner-7.0.1/xulrunner /usr/local/bin/

```Now we need to setup the library path errors (gotten from [here]("http://www.guillermomolina.com.ar/index.php/es/proyectos/extension-de-firefox-para-kwallet/103-library-path-issues"))

```
sudo su
echo "export LD_LIBRARY_PATH=/usr/lib/kde4/libkdeinit:/usr/local/lib/xulrunner-7.0.1" >> /usr/bin/firefox
exit
```If you use thunderbird, and want the same integration, you should do the same thing replacing /usr/bin/firefox with /usr/bin/thunderbird (I didn't test this, as I don't use thunderbird, but it should work).

Now exit any existing firefox windows you have running. Run firefox and install the extension from [here]("https://addons.mozilla.org/en-US/firefox/addon/kde-wallet-password-integratio/"). Restart firefox, and you should have a pop requesting access to kwallet. Allow it and you should be good.

---

