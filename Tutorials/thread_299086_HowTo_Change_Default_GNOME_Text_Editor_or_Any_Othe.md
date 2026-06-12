---
title: "HowTo Change Default GNOME Text Editor or Any Other Default Program"
date: 2006-11-13
forum: Tutorials
---

### Post by AgenT on 2006-11-13
How-To Change Default Text Editor (or any other default program)

The following step-by-step guide will make the program Scribes open every plain text document instead of Gedit. Instead of Scribes, you may use any other program.

Check if this file exists:
```
~/.local/share/applications/defaults.list
```If so, open it, if not:
```
touch ~/.local/share/applications/defaults.list
```Open ~/.local/share/applications/defaults.list and look for this entry:
```
[Default Applications]
```If it does not exist, add it on top. Next, add the following below "[Default Applications]":
```
text/plain=scribes.desktop
```Your completed entry should look like this:
```
[Default Applications]
text/plain=scribes.desktop
```Now run:
```
pkill nautilus
```It is possible to set any mime type and any program that has a *.desktop entry. Find out your favorite program's desktop entry by looking in this folder:
```
/usr/share/applications/
```You need to know what mime type you want to have your new program open. text/plain means opening up any normal text file. If you would like Scribes to open ANY text file, you would substitute text/plain with text/* and follow everything else.

Why is this better than just right-click on file -> Open With? Because with the above, ALL plain text files will be opened by Scribes, not just ones that have a particular extension.

For more details on what programs are used for what mime types, see file:
/usr/share/applications/defaults.list
One easy way to replace a program like gedit would be to get all entries containing gedit, replace them with scribes, and add that list to ~/.local/share/applications/defaults.list.

This quit one-liner does exactly that, except that it posts the results in terminal and you will just have to copy/paste it into your file:
```
 grep gedit /usr/share/applications/defaults.list | sed s/gedit/scribes/g
```

---

### Post by edmnc on 2008-03-28
Hey, thanks for this!

---

### Post by DAE51D on 2009-01-06
Could you please explain as to how to make Geany the default editor for just PHP files (NOT text files)? Currently it is defaulted to "Gedit".

I can't figure out what the mimetype should be? 
Here is what I have currently, but they don't work:

$ cat ~/.local/share/applications/defaults.list
[Default Applications]
application/x-httpd-php=geany.desktop
application/x-php=geany.desktop
text/x-php=geany.desktop

$ grep php /usr/share/applications/defaults.list
$

$ grep gedit /usr/share/applications/defaults.list
application/x-perl=gedit.desktop
text/plain=gedit.desktop
text/x-chdr=gedit.desktop
text/x-csrc=gedit.desktop
text/x-dtd=gedit.desktop
text/x-java=gedit.desktop
text/mathml=gedit.desktop
text/x-python=gedit.desktop
text/x-sql=gedit.desktop

it doesn't list PHP there at all  :confused:

---

### Post by traffas on 2009-02-12
I, too, would be very interested in making Geany the default program to handle PHP files.

---

### Post by Tominator on 2009-05-24
I want Gmail to be my default as opposed to Evolution. I followed your instruction and:


Code:

 grep gedit /usr/share/applications/defaults.list | sed s/gedit/scribes/g

I got the following:

application/x-perl=Evolution.desktop
text/plain=Evolution.desktop
text/x-chdr=Evolution.desktop
text/x-csrc=Evolution.desktop
text/x-dtd=Evolution.desktop
text/x-java=Evolution.desktop
text/mathml=Evolution.desktop
text/x-python=Evolution.desktop
text/x-sql=Evolution.desktop

I tried:


Code:

/usr/share/applications/

and got:

bash: /usr/share/applications/: is a directory

no help there, would the substition of Gmail for Evolution on my list work?

---

### Post by Mindless Automaton on 2009-06-17
> How-To Change Default Text Editor (or any other default program)

The following step-by-step guide will make the program Scribes open every plain text document instead of Gedit. Instead of Scribes, you may use any other program.


How about something like:

Navigate to /usr/share/applications in Nautilis. 
Scroll down to Text Editor.
Right-click Text Editor, select Properties.
Change the command line to your application. (in my case, medit)

EnjoY!

Mindless Automaton

---

### Post by Mindless Automaton on 2009-06-17
> **traffas said:**
> I, too, would be very interested in making Geany the default program to handle PHP files.

Does this do what you would like?

In Nautilus, find a php file.
Right-click the php file and select properties.
Select the Open With tab.
Left-click Add button.
Find Geany or set custom command to launch Geany.

Thanks!

Mindless Automaton

---

### Post by sylwester on 2009-09-10
So far all of above changes the behaviour for one user. I wanted to set smplayer as system wide multimedia player instead of totem. I did this to get the desired effect:

```

sudo perl -pi.old -e 's/^([^=]+)=totem\.desktop/$1=smplayer.desktop/' /usr/share/applications/defaults.list

```

To only change for video files one can do this:
```

sudo perl -pi.old -e 's/^(video[^=]+)=totem\.desktop/$1=smplayer.desktop/' /usr/share/applications/defaults.list

```

make sure the file smplayer.desktop (or watherver you use or change from/to) exists under /usr/share/applications/.

---

### Post by Johannes Eva on 2011-01-12
> **AgenT said:**
> How-To Change Default Text Editor (or any other default program)


There is another way to do this. It is a somewhat clumsy way but it works. As it needs a longer explanation, I have written an article about this:

_**[How to change file associations on Ubuntu]("http://www.johannes-eva.net/change-the-default-application-ubuntu-linux")**_

(Tested with Ubuntu 10.10 Maverick Meerkat)

---

### Post by nikosft on 2011-01-27
For Ubuntu 10.10 I found this simple solution to make geany your default text editor.

-In GNome menu Right Click and press Edit Menus
-Go to Accessories, Text Editor and press properties
-Change the command tou geany

Now all documents open with geany instead of gedit

Nikos

---

### Post by manech on 2011-10-21
Thanks, worked perfectly. Ubuntu Ocelot 11.10 was driving me crazy as it did not open tex-files with Kile.
Actually the tutorial did not work immediately, because the kile.desktop file is located in a **subfolder called kde4**. If you simply specify the subfolder in the default.list file, it will work. By the way: In Ocelot it is not necessary to kill Nautilus to apply the changes.
```
[Default Applications]
application/x-tex=**kde4**/kile.desktop
```

---

### Post by harlequin_ on 2011-10-26
> **manech said:**
> Thanks, worked perfectly. Ubuntu Ocelot 11.10 was driving me crazy as it did not open tex-files with Kile.
Actually the tutorial did not work immediately, because the kile.desktop file is located in a **subfolder called kde4**. If you simply specify the subfolder in the default.list file, it will work. By the way: In Ocelot it is not necessary to kill Nautilus to apply the changes.
```
[Default Applications]
application/x-tex=**kde4**/kile.desktop
```


Ah. Been looking around for this. Thanks so much.

---

### Post by giotech on 2012-01-08
To change a default editor (gedit) to any other editor  (for example, geany) 

[LIST=1]
[*]just right-click a text or php file;
[*]select "properties";
[*]select "open with" tab
[*]choose among the listed/installed text editors;
[*]click "set as defalut"
[*]click "close"
[/LIST]
Enjoy!

---

