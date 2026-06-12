---
title: "isn't AppImage just as bad as an EXE file?"
date: 2020-12-17
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2020-12-17
I haven't tried to install an AppImage yet is because I find the experience of installing an AppImage to be very similar to installing EXE files on Windows, and the install process is the same too:

To install IrfanView:
1. Go to IrfanView's homepage: [https://www.irfanview.com/](https://www.irfanview.com/)
2. Download EXE file of IrfanView.
3. Run EXE file in Downloads folder.

To install Olive Video Editor:
1. Go to Olive Video Editor's homepage: [https://olivevideoeditor.org/](https://olivevideoeditor.org/)
2. Download AppImage of Olive 0.2 Nightly Builds.
3. Run AppImage file in Downloads folder.

The install process of both EXE and AppImage files are very similar, and I'm afraid that this could lead to malware authors using AppImage to install malware on Linux easier, just like malware authors on Windows using EXE files to spread malware, and it is because of this reason why I haven't attempted to install an AppImage on my system is because I don't trust this format, since it reminds me of install EXE files in Windows.

There's also the issue of trust as well. Just like an EXE file, you download it from the developer's website, and as we've seen, a website can be hijacked and an EXE file be compromised, an example of that happening is IrfanView's website was hijacked and the EXE files were compromised, and the same thing can happen to AppImages. Now, if the AppImage comes from a repository, just like how we install Ubuntu applications from the App Store, then maybe there would be a level of trust, but for now, I won't be install AppImages any time soon.

---

### Post by TheFu on 2020-12-17
AppImage is about providing an all-inclusive, single-file, package, that can be copied to any recent Linux and run. That's the point. To my knowledge, security was never a consideration for AppImage. It is basically just like .deb files, which make up 99% of your Linux OS as installed today.  Just that .deb files specify external dependencies, that package format doesn't include the dependencies.

Any program deployment method can be hijacked, including .deb files.  We trust Canonical's repos too. Why?  For that matter, snap packages with all their constraints can also be modified to include tracking or other unwanted "features" and posted to the snap-store.

We should always get programs from trusted sources. 
Every trusted source will likely make a mistake from time to time.
Crackers will be looking for those mistakes and try to take advantage.
I'm more likely to trust a package created by the project team behind a program than anyone else. We do that every day, right? 

Instead of using IrfanView, check out **geeqie** for a native Linux viewer.
There are lots and lots of video editors. Those distributed via snap-package never work for me for unknown reasons and I cannot access my network storage with them, ever, so snaps just won't work for me. Flatpak and AppImage files are useful if the project team refuses to provide Ubuntu .deb packages for my release.

Oh - and AppImages don't support using symbolic links to the real appimage file for running. that's a huge hassle to me, but something about the way AppImages expand when run gets broken, so that doesn't work.

Most Windows security flaws aren't due to the way software is copied, but rather it is due to a lack in the security of the entire OS for programs running on the OS. Unix systems don't have that same flaw. Unix file and directory permissions have done a great deal to keep those systems secure since the early 1970s and file permissions are still core to Unix security today.

---

### Post by linuxyogi on 2021-01-04
I too am curious. The only appimage I have ever used is balenaetcher which I used to burn the Lubuntu 20.04 iso to my USB. DD was giving I/O errors I have no idea why & atm I am using 2 snaps namely Spotify & Knsip. I am too new to this packaging system. I don't yet know how to update snap packages. This is not the time to be lazy so I will Google that now.

---

