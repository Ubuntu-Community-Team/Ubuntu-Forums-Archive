---
title: "Apple vs Linux: Linux on the Iphone"
date: 2008-03-20
forum: The Cafe
---

### Post by Bungo Pony on 2008-03-20
Don't hear much about Apple & Linux wars, but it sounds worse than Windows vs Linux...


[http://www.technewsworld.com/story/mobile-tech/62209.html](http://www.technewsworld.com/story/mobile-tech/62209.html)

Android, Schmandroid: Linux on the iPhone

By Richard Adhikari
LinuxInsider 
Part of the ECT News Network 
03/20/08 4:00 AM PT 

Apple has been battling renegade Linux hackers, upgrading the iPhone's firmware every time they hack into the device. "It has been a little bit of an arms war," said Saurik, aka Jay Freeman. Will things change now that Apple has opened up its SDK to developers, welcoming the gaming community and targeting the enterprise space?

Since its launch, renegade developers have been working to make the iPhone a Linux workstation, porting tools to the device. And why not? It has enough RAM and hard disk space to make the work worthwhile.

"My iPhone has 16 GB of disk space, 128 MB of RAM, a 600-plus MHz processor and a much better display than my original computer, and it has Darwin open source ported to it; so its essentially a Unix-like OS which led guys like Jay and myself to use the phone as if it were a Unix workstation and write applications in a familiar Unix-based environment," Brian J. Fox, founder and technology partner at The Okori Group, told LinuxInsider.

Fox should know: He was the first employee at the Free Software Foundation  and, while there he wrote Bash, a Unix shell, for the GNU Project back in 1987, which has become the default shell on most Linux systems as well as on Mac OS X. He also developed Wells Fargo's (NYSE: WFC)  online banking system and has been chief technology officer at various startups.

Jay is Jay Freeman, who implored, "Call me Saurik, that's been my handle ever since I began working on computers, Jay Freeman's too common a name." Saurik is a Ph.D. student at the University of California, Santa Barbara, and a freelance technology consultant who works closely with Fox on various projects. 
 
Cydia and Telesphoreo 

Initially, several tools developed by the Free Software Foundation and used on Linux, Mac OS X and Solaris were ported to the iPhone. These were "typically binaries and programs you would expect on a computer," Saurik told LinuxInsider.

However, the porting was roughly done and "some of them didn't quite work," Saurik said.

Being a perfectionist, he "tweaked them to make them work better," then began looking at creating an administrative solution for the iPhone that would let the user add and remove tools more easily than the app.tapp installer which is commonly used on the iPhone.

Saurik selected the Debian Advanced Packaging Tool (APT) "which is used on numerous Linux installations and the one I consider to be the most stable," ported that to the iPhone and "now I have it to the point where anybody can run an APT repository in the same way you would on a machine running Debian and install what you want," he said.

Then, he wrote Cydia, a graphical front end that "lets you install and uninstall programs the same way as the app.tapp installer does," he said. Because the process of porting the tools to the iPhone was similar to building a Linux distribution -- "You have to coordinate the tools together, and decide what is and what's not a package," the workload is much too heavy for only one person, so Saurik launched a project called "Telesphoreo," an open source Unix distribution "to be launched on the modern smartphone, and the first is the iPhone," he said.

The distribution will also be targeted "to Android and the other smartphones running Linux," Saurik said. 
The Technical Details 

Cydia is a UIKit front end that provides a graphical user interface (GUI) for users to select and install programs. It isn't limited to command-line software, so it should allow the installation of any and all software package types.

Why call it Cydia? "Cydia pomonella is the scientific name for the codling moth, which is what we often think of as the stereotypical apple worm," Saurik said. UIKit is the user interface framework in the iPhone Runtime, the equivalent of AppKit for traditional OS X applications.

Saurik has bootstrapped Telesphoreo by porting "well over a hundred projects" ranging from Bash to Xeyes, "along with a number of supporting libraries and scripting languages" to the iPhone. All the source modifications made, as well as the build scripts for compiling them all, are available on the Telesphoreo subversion repository.

Subversion is a version control system used to maintain current and historical versions of files such as source code, Web pages and documentation, and is well-known to the open source community. 
The Quiet War 

Apple (Nasdaq: AAPL)  has been battling renegade Linux hackers, upgrading the iPhone's firmware every time they hack into the device.

"It has been a little bit of an arms war," Saurik said.

Will things change, now that Apple has opened up its SDK to developers, welcoming the gaming community and targeting the enterprise space?

Not really: "They're now presenting a mechanism for delivering new third-party applications to the iPhone but the method is controlled by Apple, so they will get to say what these applications can and can't do, and whether these applications can run on the iPhone," Fox said. "Not everybody will want to use the applications that Apple will deem correct for them to use; many will be looking for alternative sources of applications."

The result: "You'll see a new type of SDK that will allow specifically for the development of applications that will run on the iPhone but that won't be in line with Apple's vision," Fox predicted. "This won't be from Apple." 
Road Warrior Extreme? 

The iPhone can do anything a Linux workstation can.

"There's no reason why I can't use X/11 on the iPhone," Fox said, adding that the Java-based OpenOffice suite can be ported to the iPhone. Also, because the iPhone has a connector on its base to output to a video source, "it can be connected to a large screen and, with a Bluetooth keyboard, that's my vision for the iPhone," Fox said, adding that it would be ideal on the road.

That's a vision not fully shared by all. "The relatively large amount of screen space and the Unix foundations of the iPhone make it probably the best Unix mobile device seen thus far," Jonathan Eunice, principal IT analyst at research firm Illuminata, told LinuxInsider. "I think it's the first mobile device that makes Web 2.0 anywhere a workable proposition."

The iPhone is ideal for those trying to get administrative dashboards, remote sessions and other high information content resources, with its strong Web access and its large, highly visible display, but "I'm not sure I'd want my full IDE (integrated development environment) displayed in 480 x 320 pixels," Eunice said. "It's hard enough on my laptop, which has about 10 times the screen real estate."

It's great for travel, though: "When you travel, you don't want to schlep a laptop across the country just to hook it up to a projector," Bernard Golden, an open source expert and CEO of Navica, told LinuxInsider. "I could see it as an adjunct, and for certain niche things, it's useful, but it's not going to be as full-featured as a laptop and you won't do really complex things on it."

---

