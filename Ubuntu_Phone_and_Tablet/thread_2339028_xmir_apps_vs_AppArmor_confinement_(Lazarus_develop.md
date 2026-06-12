---
title: "xmir apps vs AppArmor confinement (Lazarus development for Ubuntu Phone)"
date: 2016-10-04
forum: Ubuntu Phone and Tablet
---

### Post by kris16 on 2016-10-04
[COLOR=#212121][FONT=Roboto]I'd like to showcase a way to develop software for Ubuntu Phone that is alternative to using Ubuntu SDK - with Lazarus IDE powered by Free Pascal.
[/FONT][/COLOR]Form my blog post:
[COLOR=#212121][FONT=Roboto](...)[/FONT][/COLOR]
[COLOR=#212121][FONT=Roboto]Now the absolute mind-blowing part: what is the default, standard, encouraged and promoted way to make apps for Ubuntu Phone? well, it is the Ubuntu SDK off course. Have you seen it maybe? Perhaps tried? well, I have. And let me tell you this about it:[/FONT][/COLOR]

[COLOR=#212121][FONT=Roboto]1. IDE is nowhere as good as Lazarus IDE[/FONT][/COLOR]
[COLOR=#212121][FONT=Roboto]2. You can't run it (the IDE) ON your Ubuntu Phone[/FONT][/COLOR]
[COLOR=#212121][FONT=Roboto]3. Once you've written an app, you can't also compile it for Windows, MacOS and bunch of other operating systems just like that[/FONT][/COLOR]
[COLOR=#212121][FONT=Roboto]4. PERIOD.[/FONT][/COLOR]

[COLOR=#212121][FONT=Roboto]So that is why Free Pascal and that is why Lazarus. Write once, compile everywhere. Enjoy![/FONT][/COLOR]
[COLOR=#212121][FONT=Roboto](...)[/FONT][/COLOR]
source: [http://kriscode.blogspot.tw/2016/10/lazarus-development-for-ubuntu-phone.html](http://kriscode.blogspot.tw/2016/10/lazarus-development-for-ubuntu-phone.html)

So I have successfully wrote compiled and deployed programs made with Lazarus on Meizu MX4 Ubuntu Edition phone. However, I cannot get to publish them via Ubuntu App Store. 
When I create click package, it results in not running my app via xmir under AppArmor confinement. I don't know how to create a suitable profile that would solve this.

As far as snap goes, I'm still learning about it. I really wish it was made easy to run x11 apps via xmir on the phone as 1st class members alongside native ones. Well, under AppArmor anyways, because without it the problem doesn't exist.
Was hoping someone could contribute and help me find a way to publish x11 apps meant for running with xmir on the phone in the Ubuntu App Store. This is not specific to any development language/tool, but generally to x11 apps that are designed to look and feel good under Xmir on the Ubuntu Touch device.
[COLOR=#212121][FONT=Roboto]&#65279;[/FONT][/COLOR]

---

### Post by KanedaSan on 2016-10-06
You should try contact Michael Zanetti who created the Ubuntu Touch Open Store.
[https://open.uappexplorer.com/](https://open.uappexplorer.com/)
Maybe he could help you with your problem, lot apps here are "apparmor unconfined".

---

