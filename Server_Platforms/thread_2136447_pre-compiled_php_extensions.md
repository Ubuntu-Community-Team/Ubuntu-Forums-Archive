---
title: "pre-compiled php extensions"
date: 2013-04-17
forum: Server Platforms
---

### Post by bquade on 2013-04-17
I have always installed php by compiling it first with *configure, make and make install*. But recently it has become harder and harder to compile (or install via apt-get) all the dependencies I need to compile the application. My webhost (Bluehost) has their system set up so that I can add a line to my php.ini file to add an extension, with no requirement that the web server be restarted and nothing to compile or download. This would make my development process go so smoothly because it would not take me a whole day to compile a bunch of downloaded code just to add a php extension.

But the best documentation I have found Ubuntu is [https://help.ubuntu.com/12.04/serverguide/php5.html](https://help.ubuntu.com/12.04/serverguide/php5.html). However, that only tells me how to install php and hook it up to apache, not how to set it up so I can add extensions on the fly. And it mentions a [COLOR=#333333][FONT=monospace]libapache2-mod-php5 package and php5-mysql package that were never needed with the compiled installation. So it is making me nervous about following those directions that only tell me how to install but not how to add extensions and it requires components that I have never used before in my current setup. I'm worried that the packaged version of php might not work well with my compiled version of apache. I am also worried that I would install the Ubuntu php packages over the compiled installation of php and it will leave the system in a state where nothing works at all because two different php installations are installed somehow. I also still use the compiled version of apache. Will I need to change that to the Ubuntu package too so that it can interface with the libapache2-mod-php5 package?

I don't want to leave the system in an unusable state because I don't have much time to make these changes, but I don't know the best way to transition from a compiled installation of php5 to using the pre-compiled packages and extensions.[/FONT][/COLOR]

---

