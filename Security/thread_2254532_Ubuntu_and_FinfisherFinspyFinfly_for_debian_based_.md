---
title: "Ubuntu and Finfisher/Finspy/Finfly for debian based OSs"
date: 2014-11-27
forum: Security
---

### Post by pull0betty on 2014-11-27
Since wikileaks has posted the finfisher aka finspy and finfly trojan horses, one of them being designed for debian based OSs, I wonder whether Ubuntu developers did something against those trojan horses, now that there is access to them. I have only tested the Windows Version of those trojan horses in a virtual machine and can happily say that Kaspersky will detect them and delete them immediately!  [https://wikileaks.org/spyfiles4/index.html](https://wikileaks.org/spyfiles4/index.html)  EDIT: the debian based application is a relay not a trojan horse.. so my question kinda makes no sense then..   Now I wonder what ways there would be for (especially a debian based) linux to get infected or whether there was an infection possible... I don't think that "wine" would work.. no root access to the system.. (as one suggested in an older already closed post) But Gamma claims to be able to infect macs and linux equally

---

### Post by bashiergui on 2014-11-27
> I have only tested the Windows Version of those trojan horses in a virtual machine and can happily say that Kaspersky will detect them and delete them immediately! Kapersky will find the specific hash of the version they know about. They won't find the same malware if a few comments or some padding is added before compiling. Understand that you're kind of protected if somebody rolls out a known version. But that would be pretty stupid  of the attacker and probably won't happen that way.

Your best bet to protect yourself from this kind of threat on Windows, Mac, and linux is to prevent malicious actions instead of trying to stop individual malicious executables. Apparmor is a good way to prevent apps from doing malicious things in linux. EMET has the same end result in windows.

You'll never win and you'll drive yourself mad chasing individual threats.

---

### Post by pull0betty on 2014-11-27
I don't think that the people at gamma are the brightest exploit developers, seeing how their mac version acted (significantly slowing down performance, using up some gb of screenshots in homefolder when no internet connection was available and such) their first versions of finfisher wouldn't even encrypt data transfer.

I wonder how eager they are in rewriting some lines, my guess is they will take a while. And yes apparmor has been there for some time now, but it seems it has not prevented a possible infection with finspy, if the claims of gamma are true (Linux boxes and macs would need to be physically accessed, at least that's what I understood in one of Appelbaum's speeches) And back in the days of preinstalled JRE on macs (snow leopard was the last one to have that?) being in the same local network with a mac you could just do about anything to them :)

---

### Post by jamal5 on 2014-11-28
Although Finfisher does supposedly work on Linux, I think actually getting it on to the system would be extremely difficult, barring physical access.

It's not as if a dirty email attachment is going to be able to install anything, it's extremely difficult to install any malware on a linux box unless the user downloads an infected PPA. Flash and java exploits exist, but those are relatively easy to prevent and I don't think that they're even a vector known to be used to install Finfisher or the like. 

Does anybody know of any realistic way a Linux user could actually be infected with Finfisher without doing something stupid (downloading programs outside of apt-get, giving attacker physical access)?

---

### Post by bashiergui on 2014-11-29
> Does anybody know of any realistic way a Linux user could actually be infected with Finfisher without doing something stupid (downloading programs outside of apt-get, giving attacker physical access)?Yes zero days.


Finfisher has versions to infect every operating system including linux. We don't know how specifically Finfisher infects linux because the tool kit has not been publicly released (the Finfisher author, Gamma, had their source code leaked but only pieces of the toolkit have been analyzed). They *could* be using zero days. If that's the case then that answers pull0betty's question whether Ubuntu or Debian has done anything to defend against it. You can't develop a patch for a zero day if you don't know about the zero day.


TIME FOR A REALITY CHECK


Finfisher is used in nation state spying, most likely by spy agencies. Brace yourselves for the truth... Spy agencies spy! 


If you are a political dissident, whistleblower, or a journalist interviewing them, then you might be concerned about Finfisher. If you're not an enemy of any governments, then you should have no concerns about government sponsored spyware.
> I wonder how eager they are in rewriting some lines, my guess is they will take a while.A government funded spy tool will get rewritten whenever it needs to be.


Finfisher is a very expensive (&#8364;1.4 million) tool. Finfisher or any of its cousins are not going to be used on anyone other than highly valuable targets. 100% of the people reading this post don't have to worry about it. You should instead focus on threats that are real to linux desktops and servers, none of which are government sponsored. You can defend against those real threats using very basic security measures such as updating software often, secure services facing the internet, don't use default configurations, strong passwords and keys, install trusted software from trusted sources, two factor authorization where possible, encrypt everything everywhere you can. And like I said earlier, prevent malicious behavior with apparmor.

---

### Post by HermanAB on 2014-11-30
I can only second AppArmor and SELinux.  Also use 'full disk' encryption and long passwords - at least 12 characters.

---

