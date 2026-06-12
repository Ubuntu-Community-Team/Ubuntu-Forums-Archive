---
title: "[video]  Google Tech Talk about creating Debian Packages"
date: 2007-05-07
forum: The Cafe
---

### Post by jiminycricket on 2007-05-07
"Anatomy of a Debian package"

Video: [http://video.google.com/url?docid=-6726522426109060914&esrc=sr1&ev=v&q=ubuntu+packaging&vidurl=http://video.google.com/videoplay%3Fdocid%3D-6726522426109060914%26q%3Dubuntu%2Bpackaging&usg=AL29H230dA_rTIPnfystS12SCm-U_Tk4hw](http://video.google.com/url?docid=-6726522426109060914&esrc=sr1&ev=v&q=ubuntu+packaging&vidurl=http://video.google.com/videoplay%3Fdocid%3D-6726522426109060914%26q%3Dubuntu%2Bpackaging&usg=AL29H230dA_rTIPnfystS12SCm-U_Tk4hw)

PDF: [http://jon.oxer.com.au/sb/modules/talks/attachments/30/20060721-Google-DebianPackages.pdf](http://jon.oxer.com.au/sb/modules/talks/attachments/30/20060721-Google-DebianPackages.pdf)

OCR of the PDF: [http://72.14.205.104/search?q=cache:CJOUH1-YO28J:jon.oxer.com.au/sb/modules/talks/attachments/30/20060721-Google-DebianPackages.pdf](http://72.14.205.104/search?q=cache:CJOUH1-YO28J:jon.oxer.com.au/sb/modules/talks/attachments/30/20060721-Google-DebianPackages.pdf)

I think this is a great talk.  It's motivating me to try to and create debian packages for Ubuntu for some programs not in the repositories.  Page 14 is where it really gets into how to create a package, "Building A Package"

---

### Post by Somenoob on 2007-05-07
Great video

---

### Post by go_beep_yourself on 2007-11-25
I watched the video.

And I have several questions about what was being said. After I understand these questions, I'll watch the video again, and hopefully it will make more sense to me.

[LIST=1]
[*]What does arbitrarily mean in the videos context?
[*]watch.ex allows you to know when knew versions are released. How would you know?
[*]What is the other type of secure shell other than ssh?
[*]What is a source tree?
[*]What are lintian and linda checks?
[*]What is tla-buildpackage?
[*]How can cvs-buildpackage be used with dh_make or is dh_make not needed?
[*]Is there a debian maintainers mailing list?
[*]What are buildfarms of debian and ubuntu?
[*]How can signatures be checked on packages?
[*]Why should deselect be used instead of apt?
[*]What is a upstream version of a debian package?
[*]What is bootstrap?
[*]What is place holders and build helper scripts?
[*]What is compatibility version in the compat file?
[*]When do the .ex files such as debian/init.d.ex need to be renamed to debian/init.d?
[/LIST]

---

### Post by pelle.k on 2007-11-25
Even though i haven't watched the video yet (i am going to though), i'll try to answer a few of your questions.

2. A properly configured "watch" file lets you run "uscan" to check for new source packages. (Debian New Maintainers' Guide, 5.10)
4. It's the (unpacked) source dir, and it's subdirectories.
5. They check for inconsistencies in the .deb and will let you know if it "seems" to be in order.
12. A package updated with a new source version.
13. Creating a "minimal" installation. Can be useful to have a clean build environment for every new package you build.
15. compat sets the lower limit on what helper scripts the package can be used to build (and was used to build, in the first place) the package with.
16. because they are just that. .ex as in .example. init.d.ex is an example init script (or daemon if you will), so you will probably not need this very often. *if* you need it, you probably know what you're doing anyway.

Further recommended reading if you're interested in building packages is;
[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html) (very thorough, very heavy reading)
[http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382) (a very good starting point. good examples)
[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html) (again, some heavy reading)

Truth to be told, you don't have to know everything from these manuals to build many packages. But i am glad i've read most of it anyway.
I use pbuilder, and most of the time i use debian unstable source packages (debianizing on your own source can be a pain in the behind, and it's easy to make mistakes.), and go from there. Another way is to use a current ubuntu package and bump it's source "upstream".

There was a learning curve, but i've got the hang of the essentials of it now anyway.

---

### Post by dfreer on 2007-11-26
> **go_beep_yourself said:**
> 
[LIST=1]
[*]What does arbitrarily mean in the videos context?
[*]watch.ex allows you to know when knew versions are released. How would you know?
[*]What is the other type of secure shell other than ssh?
[*]What is a source tree?
[*]What are lintian and linda checks?
[*]What is tla-buildpackage?
[*]How can cvs-buildpackage be used with dh_make or is dh_make not needed?
[*]Is there a debian maintainers mailing list?
[*]What are buildfarms of debian and ubuntu?
[*]How can signatures be checked on packages?
[*]Why should deselect be used instead of apt?
[*]What is a upstream version of a debian package?
[*]What is bootstrap?
[*]What is place holders and build helper scripts?
[*]What is compatibility version in the compat file?
[*]When do the .ex files such as debian/init.d.ex need to be renamed to debian/init.d?
[/LIST]

**8. Is there a debian maintainers mailing list?** - [http://lists.debian.org/debian-mentors/](http://lists.debian.org/debian-mentors/) is probably what you are looking for. Beyond that, if you have questions about maintaining a specific package and wish to use a mailing list, this may be of use:
[http://www.debian.org/MailingLists/subscribe](http://www.debian.org/MailingLists/subscribe)

**9. What are buildfarms of debian and ubuntu?** I'd need to know the context this was used in to be sure, but I'm guessing it is referring to clusters of computers used to build packages. As I understand the way official packages are built, maintainers upload the source of a package, along with the diff file for arch/debian compatibility, and a "build farm" would make the actual .deb. I could be way off base, but I need to watch the entire video yet again.

EDIT: Ok, basically source packages are sent to debian, and since debian supports SPARC, amd64, i386, etc etc, instead of having the maintainer build a .dev for each architecture individually, they send the source package to "build farms" which will compile the packages for all the architectures supported.

**11. Why should deselect be used instead of apt?** - As the poster on the debian forums stated in that link you sent me, deselect (actual package name in ubuntu is dselect) is a high-end package management tool, like add/remove programs or synaptic. dselect IMO can be considered the synaptic of the CLI. 

When the speaker in the video said "apt is not intended for a end user tool" (~4:25-5:20) it does not mean that "apt should not be used, dselect or synaptic should be used".

dselect and synaptic are considered "high-level", because they build upon apt (mid-level) and dpkg (low-level). dselect, btw if you have never used it, is the CLI equivilent of synaptic, using ncurses or something similiar to create a menu.

Now, ubuntu is designed to be as user-friendly as possible, and to have a GUI way of doing things. Since apt is not considered to be user friendly (in the sence you have to open a terminal to use it), it is not **intended** for end-user usage. But as you probably already know, apt is far more useful and quicker to use than opening up synaptic, which is why most users end up using apt instead of synaptic.

Since dselect is a CLI tool, it is pretty much obsolete IMO. I mean, why open dselect when you already have the terminal open?


I'm off to watch more of the video once again. But really, this video isn't so much a "How to make debian packages" as an "What is a debian package, since I'm used to making RPM's and haven't had much experience with a debian-based distro before" IMO. There are far easier ways of making packages, depending on the package being built and the reason you are making the package.

EDIT:
**12. What is a upstream version of a debian package?** - Let's use zsnes in the official ubuntu repositories as an example.
The upstream version of a program, at least the furthest upstream version would be the original source code distributed by the developer's of zsnes. The next version, downstream from the source code but upstream from ubuntu, is the debian package in the debian repositories (made by a maintainer who compiled zsnes from the source code). The last package would be ubuntu's, the furtherest downstream, who modified the debian package to specifically work for ubuntu.

When it talks about the hyphen, look at zsnes again. Zsnes is currently version 1.51, and I have released quite a few packages of zsnes 1.51 since I make mistakes. So my packages look like this:
zsnes_1.51-3.1_gutsy-amd64.deb
3.1 is my downstream version number, since I use the official source and I don't repackage the debian zsnes .deb I don't include their version number.

**6 & 7. What is tla-buildpackage? How can cvs-buildpackage be used with dh_make or is dh_make not needed?**
dh_make should help you in making a debian package out of a source tarball, like zsnes_1.51.tar.gz, although I haven't used it myself. Sometimes, you will want to make a package from an unofficial release, which is what cvs-buildpackage would help you with (CVS/SVN is basically the source code online from what I understand of it. it helps multiple developer's that are working on a single package keep track of the latest code added by others, and allows them to download the latest source code all at once, described as a "CVS/SVN checkout". So basically, grabbing source from an CVS would give you the latest features, but it could very well be unstable). tla-buildpackage has something to do with making a debian package from ARCH archives.

I've only checked out source code before, never contributed, so someone else may correct anything I got wrong.

---

