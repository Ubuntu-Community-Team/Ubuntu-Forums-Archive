---
title: "Submitting an Application to Debian Mentors"
date: 2020-05-04
forum: Ubuntu Application Development
---

### Post by ChrisOfBristol on 2020-05-04
I've produced an application and I have turned it into a Debian style package - a .deb file. It was available on GetDeb when that was going and got downloaded a lot.

I have since carefully satisfied all the Debian file requirements I can think of, signed up for Debian Mentors and hoped for a sponsor/mentor without success. Am I going about this the right way? I am wondering whether perhaps I am trying to get into Debian at a high level suitable for essential packages, when it may be possible to submit my rather less significant package where it might only get into Ubuntu at a lower level.

I have also been assisting the author of another application which would otherwise only be available for Windows and macOS by providing a deb for it. He would like to do the same for his application, he says "Can we include it in the official release?". I would like to be able to give him some advice/help, but despite spending days reading Debian documentation to find out whether my approach is wrong, I haven't got any further, I find the links in the endless documentation just took me round in circles and eventually back to the first document.

---

### Post by TheFu on 2020-05-04
Ubuntu is related to debian, but NOT debian.  I’ve never used getdeb - never.

The vast majority of people here are end-users.  I’d guess perhaps 10 developers and nobody from Canonical are here.
in my developer, but not packager, experience here, I’d expect that creating a PPA for each package would be the expected route to eventually become popular and become part of an official repo after a few years.   

A shorter way may be to create a snap package, Flatpak package and Appimage package.  All three. There are negatives for these and the PPA method. Each as a community of users.  Snaps mostly flow into Ubuntu. Flatpaks mostly into Fedora.  When a snap doesn't work for my needs, i seek out an appimage, though they have flaws too.

May take a look at the **mkusb** tool which is popular in these forums.  I don't use it, but respect the creator and see very good reasons for it. Check the path it followed for ubuntu packaging.

---

