---
title: "Chrome seems to default to Bing"
date: 2019-04-18
forum: Security
---

### Post by jarp53 on 2019-04-18
not sure if i'm in the right forum; but  the searches on chrome are being hijack by BING , this did not happen before and it was not until I upgraded , first to 18.04 then to 18.10 ; I did all the things recommended on the web even uninstall some apps even when i reset chrome settings to default but  still nothing. so i use Synaptic manager and remove the stable version, and install the unstable one and that works , so i was curios to see what happen if i install from google but Ubuntu always wants to install  the one from their software and that's when i notice that version comes already with the malware in  it , Am I the only one with this problem ? I don't  see any ost about this

---

### Post by yetimon_64 on 2019-04-18
On any version of google chrome, either from the repos or directly from google, this problem should be fixable from the settings menu within the google chrome browser itself without the need to uninstall etc. Resetting to default settings won't help if the default is set to bing by whoever you are sourcing the browser from. Sounds like different sources of the browser may be setting a different default search engine which is easily changed locally.

Go to the tools menu, the 3 vertical dots at the top right of the browser, and select "Settings" > Scroll down to the "Search Engine" settings section and click on the drop down menu to set which engine you want used in the address bar. See screenshot ...
[ATTACH=CONFIG]283053[/ATTACH]

Then go to the next setting "Manage Search Engines" and set whichever search engine you want to be used as default.
See screenshot ...
[ATTACH=CONFIG]283054[/ATTACH]
To set an engine as your default use the 3 vertical dots menu to the right of the engine you wish to set and select "Set as default", this will stop Bing "hijacking your searches". You can add or remove engines from this section as needed. See next screenshot, note bing and yahoo are now missing, I chose the option to "Remove from list" for them as I never use either of them :-)...
[ATTACH=CONFIG]283055[/ATTACH]

If you have a problem locating the "3 vertical dots" I mention above for the main settings menu then you can alternatively type "chrome://settings" (without the quotes) into the address bar and press "Enter" to get it up as well.

Regards, yeti.

---

### Post by jarp53 on 2019-04-18
thanks ;  but i have done all of that . and it looks like this happens to a lot of people fortunately by trying to upgrade to 19.02 I broke my OS , so I reinstall 18.04 from scratch and now the problem is gone

---

### Post by rbmawby on 2019-06-12
I have a similar problem with yahoo but this approach does not deaal with the redirect to _ 
[https://search.hmyweatherhomepage.com/?uc=20190420&ap=appfocus84&source=-bb9&uid=bfd4829d-fafd-4f11-b4f0-923e81b00a79&i_id=weather_1.2&cid=bnehfdjkgammlikmnocbdegooonbpidm&page=newtab&](https://search.hmyweatherhomepage.com/?uc=20190420&ap=appfocus84&source=-bb9&uid=bfd4829d-fafd-4f11-b4f0-923e81b00a79&i_id=weather_1.2&cid=bnehfdjkgammlikmnocbdegooonbpidm&page=newtab&)

---

