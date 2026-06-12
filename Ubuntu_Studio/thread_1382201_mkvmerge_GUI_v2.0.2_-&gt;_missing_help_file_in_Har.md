---
title: "mkvmerge GUI v2.0.2 -&gt; missing help file in Hardy"
date: 2010-01-15
forum: Ubuntu Studio
---

### Post by webpilot on 2010-01-15
Hi all,

I have been using 8.04 LTS since February 2009, and today, I needed these tools.

**mkvtoolnix-gui**
    *Set of tools to work with Matroska files - GUI frontend*

I installed them using Synaptic.    They are an older version.  To run I left mouse clicked (lmc) Applications - Sound & Video - MKV files creator.  This went all well and good.

However, from within the program, after I clicked on _H_elp - _H_elp (or pressed the F1 key), I received the following error message 

> The mkvmerge GUI help file was not found. This indicates that it has never before been opened, or that the installation path has been changed since.

Please select the location of the 'mkvmerge-gui.hhp' file.OK, fine.  I searched my system (Places - Search for Files) and could not find this file anywhere.

I clicked on _H_elp - _A_bout and found

> mkvmerge GUI v2.0.2 ('You're My Flame')
built on Jul  3 2007 05:57:30I've had this problem before with other softwares and hoped I could find a source download with the missing documentation.  

I found it on the [www.bunkus.org]("http://www.bunkus.org") website and can be downloaded from this [page]("http://www.bunkus.org/videotools/mkvtoolnix/sources/") .  The file you want to download is [mkvtoolnix-2.0.2.tar.bz2]("http://www.bunkus.org/videotools/mkvtoolnix/sources/mkvtoolnix-2.0.2.tar.bz2") .  Download the file and remember where you saved it.  

Using Nautilus, navigate to the location of the file. Right mouse click the file and lmc *Extract Here* .  Navigate to the **doc** file folder and you will find *mkvmerge-gui.hhp* .  You may want to download this file, [mkvmerge's documentation]("http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge.html"), into this **doc** file folder also.  

I downloaded my .bz2 file into the folder, *~/downloads/mkvtoolnix-2.0.2 *.  After extraction, all the files went into the directory, *~/downloads/mkvtoolnix-2.0.2/mkvtoolnix-2.0.2* .  To save hard drive space, I deleted all of the directories there save for three, namely, **doc**, **examples** and **test**.

Launching Applications - Sound & Video - MKV files creator again and pressing F1, this time lmc the OK button.  You will be prompted to "Choose the location of the mkvmerge GUI help files" and navigate to where your doc directory resides.  Click OK.

A window entitled "**Help: A guide to mkvmerge GUI**" will appear.

Cheers

*PS*  *Remember there are **examples** and **test** directories to explore, now*

---

### Post by MestreLion on 2012-02-02
VERY informative, thank you!

For Natty and beyond, there is no need for this anymore, as the docs, examples and guide were included in the repos (part of mkvtoolnix and mkvtoolnix-gui).

I wonder why the documentation (and the .hhp file) were left out for Maverick, Lucid and Hardy. Maybe they were planning on building a separate mkvtoolnix-doc package and gave up?

Just an update for Lucid and Maverick users: instead of downloading the suggested mkvtoolnix-2.0.2.tar.bz2, go to the sources page and download the version that matches *YOUR* installed mkvtoolnix (use **apt-cache policy mkvtoolnix** or **mkvinfo --version**). For maverick, thats [mkvtoolnix-4.0.0.tar.bz2]("http://www.bunkus.org/videotools/mkvtoolnix/sources/mkvtoolnix-4.0.0.tar.bz2")

Last but not least, I also recommend that after following webpilot's steps, they should be moved to the proper, system-wide location, **/usr/share/doc/mkvtoolnix-gui/** for the **guide** and **/usr/share/doc/mkvtoolnix** for the **examples**. Or course, root privilege will be required for that.

In a nutshell:
```
version=$(mkvinfo --version | cut -d' ' -f2 | cut -d'v' -f2)
wget "http://www.bunkus.org/videotools/mkvtoolnix/sources/mkvtoolnix-${version}.tar.bz2"
tar -xf "mkvtoolnix-${version}.tar.bz2"
sudo cp -r "mkvtoolnix-${version}/doc/guide" /usr/share/doc/mkvtoolnix-gui
sudo cp -r "mkvtoolnix-${version}/examples" /usr/share/doc/mkvtoolnix
rm -r "mkvtoolnix-${version}"*
```The **tests** directory, IMHO, are not needed, since they are intended for testing the executable, meant for developers only, and, above all, *they require sample data files that are not present* in neither Ubuntu repo nor upstream package.

Hope that helps!

---

