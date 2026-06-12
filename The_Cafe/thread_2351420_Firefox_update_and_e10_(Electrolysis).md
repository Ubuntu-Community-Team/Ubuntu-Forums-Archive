---
title: "Firefox update and e10 (Electrolysis)"
date: 2017-02-03
forum: The Cafe
---

### Post by motang on 2017-02-03
As you may know Mozilla released Firefox 51 this past Tuesday. When I came home from work yesterday evening I my system had already update and Firefox 51 was ready for me to use. At work I had done an update manually (Windows 10) and went from 32bit to 64bit (finally) and noticed e10 was enabled by default. So I was enjoying the speed and multi processing that it brought. I was curious at home and when I looked I saw that it was disabled because of addons. I don't use much so I disabled all but the Ubuntu specific ones, and restarted. Still same, so I went ahead and disabled all addons, and after doing so, I had e10 enabled! Firefox is SO MUCH more faster and responsive now, it feels like a whole new browser.  Thanks for reading and what I am getting at with this long post, is try disabling all your addons and see if you get e10, you can check by typing in about:support ([http://imgur.com/a/IXz7s](http://imgur.com/a/IXz7s)) in the URL bar.

---

### Post by vasa1 on 2017-02-03
Your image has *2/2 (enabled by default)*. I have *1/1 (enabled by default)*. I wonder what's the difference. Could it be that I have extensions enabled and that all these extensions are "e10 compatible"?

```
Extensions
----------

Name: Application Update Service Helper
Version: 1.0
Enabled: true
ID: aushelper@mozilla.org

Name: Classic Theme Restorer
Version: 1.6.1
Enabled: true
ID: ClassicThemeRestorer@ArisT2Noia4dev

Name: Greasemonkey
Version: 3.9
Enabled: true
ID: {e4a8a97b-f2ed-450b-b12d-ee082ba24781}

Name: Multi-process staged rollout
Version: 1.7
Enabled: true
ID: e10srollout@mozilla.org

Name: Pocket
Version: 1.0.5
Enabled: true
ID: firefox@getpocket.com

Name: Stylish
Version: 2.0.7
Enabled: true
ID: {46551EC9-40F0-4e47-8E18-8E5CF550CFB8}

Name: uBlock Origin
Version: 1.10.6
Enabled: true
ID: uBlock0@raymondhill.net

Name: Web Compat
Version: 1.0
Enabled: true
ID: webcompat@mozilla.org

```I should mention that my Firefox is direct from Mozilla and not the one supplied by the Software Center which has Ubuntu-specific extensions.

Edit: After opening another Firefox window, I see 2/2 and 3/3 after opening a third. So the denominator refers to the number of open windows and the numerator (I had to Google for that after all these years!) refers to those that are multiprocess.

---

### Post by motang on 2017-02-04
> **vasa1 said:**
> Your image has *2/2 (enabled by default)*. I have *1/1 (enabled by default)*. I wonder what's the difference. Could it be that I have extensions enabled and that all these extensions are "e10 compatible"?
...

I should mention that my Firefox is direct from Mozilla and not the one supplied by the Software Center which has Ubuntu-specific extensions.

Edit: After opening another Firefox window, I see 2/2 and 3/3 after opening a third. So the denominator refers to the number of open windows and the numerator (I had to Google for that after all these years!) refers to those that are multiprocess.

Was going to tell you that opening more windows will up the numbers. So how is yours direct from Mozilla? Did you download the .tar file and just launched it?

---

### Post by vasa1 on 2017-02-04
> **motang said:**
> Was going to tell you that opening more windows will up the numbers. So how is yours direct from Mozilla? Did you download the .tar file and just launched it?
That's about it.

---

