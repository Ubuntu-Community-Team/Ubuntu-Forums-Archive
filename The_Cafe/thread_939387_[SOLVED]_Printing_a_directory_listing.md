---
title: "[SOLVED] Printing a directory listing"
date: 2008-10-05
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2008-10-05
I would like to be able to print all the information that is supplied by the file manager. Filename, date accessed, size in bytes. I tried to find a way to do this about a week ago and couldn't.

thanks for your time.

---

### Post by yabbadabbadont on 2008-10-05
If you can figure out the correct options to get ls to show what you want, then you could pipe it's output to lpr in a terminal window.

---

### Post by cardinals_fan on 2008-10-05
Do you mean print as in printing a paper copy using a printer, or print as in list in the terminal?

---

### Post by zmjjmz on 2008-10-05
If you look in man ls you'll find some nice switches that will get ls to print a lot of data.

---

### Post by Trail on 2008-10-06
Try```
ls -lat > ~/print_file
```, which will create a file named print_file on your home directory with some info on the directories and files.

---

### Post by fatality_uk on 2008-10-06
This is what you are looking for I think.
For instance, if you want to output the contents of your desktop dir to a file, use this below:

> cd Desktop
ls -ltr > ~/fm_dir_list.txt

---

### Post by Mark_in_Hollywood on 2008-10-06
Everybody who has posted so far missed my point. 

I want to go to Places, then Home Folder and then any subfolder, open that and have a print command in the Gnome File Manager. 

Help move Ubuntu forward away from command line for such simple tasks.

Thanks, community.

---

### Post by fatality_uk on 2008-10-06
Ahhh, ok so you want a menu item that says "Print directory listing..."
Your second explination was clear.

---

### Post by cardinals_fan on 2008-10-06
> **Mark_in_Hollywood said:**
> Everybody who has posted so far missed my point. 

I want to go to Places, then Home Folder and then any subfolder, open that and have a print command in the Gnome File Manager. 

Help move Ubuntu forward away from command line for such simple tasks.

Thanks, community.
You still haven't said what you mean by 'print'...

---

### Post by zmjjmz on 2008-10-06
I suppose you could write a nautilus script to do that.
```
#!/bin/sh
cd $NAUTILUS_SCRIPT_CURRENT_URI
ls -ltra > ~/Desktop/Nautilus\ Directory\ Listing.txt

```
But for me it only prints ```
total 12
drwx------ 2 zj1992 zj1992 4096 2007-11-12 21:54 Desktop
drwx------ 3 zj1992 zj1992 4096 2007-11-12 21:54 ..
drwx------ 3 zj1992 zj1992 4096 2007-11-12 21:54 .

```

Anyone know how to fix that?
EDIT: Actually it works fine.
But not when printing the contents of ~ for some reason.

---

### Post by Mark_in_Hollywood on 2008-10-06
I want to print a listing of all the files in a directory. I want to print it to a piece of paper or to an .odt file. I would like the standard printer window to open and offer a choice of print to file (which is much like a screenprint). 

By way of example, I have in a folder called: pdf, a sub-folder called Agriculture. In the folder: Agriculture there are about 50 documents. I want a print-out, neatly formatted for the 8 1/2 X 11 inch page. 

Sorry to have not been clearer earlier.

---

### Post by bruce89 on 2008-10-06
```
ls -lRt | lp
```

---

### Post by Trail on 2008-10-07
> **Mark_in_Hollywood said:**
> Help move Ubuntu forward away from command line for such simple tasks.

How about: no.

Why go through all that effort of making a script or a plugin or whatever when doing such a simple task equals just typing 10 characters on a terminal.

Then on Monday you want to also print hidden files and folders, on Tuesday you don't want to. Will you change the script? On Wednesday you want a recursive scan, other times you don't. Friday you want the output sorted. Isn't it easier to type an extra 'a' or 'r' whenever needed?

Then, one day, you decide to ditch Nautilus and use a different file manager. Your script won't work. What are you going to do afterwards? Rewrite it again? And what when you decide to use KDE/XFCE/etc. Or you want to do the same on a friend's PC.

You should stop being paranoid about the command-line; it is a very powerful, universal toolbox, were you can combine basic programs to create a `chain' that accomplishes a task you want. And if you avoid it for simple tasks such as these, you have no chance at all to understand and use it for complex tasks.

---

### Post by graabein on 2008-10-07
> **Mark_in_Hollywood said:**
> I want to print a listing of all the files in a directory. I want to print it to a piece of paper or to an .odt file. I would like the standard printer window to open and offer a choice of print to file (which is much like a screenprint).

May I suggest you go straight to the source, namely the [GNOME Bugzilla]("http://bugzilla.gnome.org")?

IMO Trail has some good points. You should spend some time to learn the basics of the shell.

---

### Post by koenn on 2008-10-07
> **graabein said:**
> 
IMO Trail has some good points. You should spend some time to learn the basics of the shell.
or just do PrintScreen

---

### Post by Mark_in_Hollywood on 2008-10-07
> **koenn said:**
> or just do PrintScreen

How does that print all the files in a directory when there are more files than can be displayed on screen at one time?

---

### Post by Mark_in_Hollywood on 2008-10-07
> **bruce89 said:**
> ```
ls -lRt | lp
```

At one time, before Linux, I had (I won't mention the OS name), Word Perfect. Now that company sold an add-on called Word Perfect Library. And if you wanted to print all the files in a directory, all you had to do was click the File Menu and pull the bar down to the "print".

---

### Post by Mark_in_Hollywood on 2008-10-07
> **Trail said:**
> How about: no.

Why go through all that effort of making a script or a plugin or whatever when doing such a simple task equals just typing 10 characters on a terminal.

Then on Monday you want to also print hidden files and folders, on Tuesday you don't want to. Will you change the script? On Wednesday you want a recursive scan, other times you don't. Friday you want the output sorted. Isn't it easier to type an extra 'a' or 'r' whenever needed?

Then, one day, you decide to ditch Nautilus and use a different file manager. Your script won't work. What are you going to do afterwards? Rewrite it again? And what when you decide to use KDE/XFCE/etc. Or you want to do the same on a friend's PC.

You should stop being paranoid about the command-line; it is a very powerful, universal toolbox, were you can combine basic programs to create a `chain' that accomplishes a task you want. And if you avoid it for simple tasks such as these, you have no chance at all to understand and use it for complex tasks.

Kinda nasty response.

Let's just for a moment assume I'm competent to use the command line. And I can issue an ls to the lpt. Good enough. But why does EVERYBODY have to be able to do this? The rest of your post about "hidden on Tuesday" isn't all that important. Just as I can do a Ctrl-H and get the hidden directories from within the Gnome file mgr. window, I can just as easily reverse that. Either way, the File "command" in the file manager ribbon bar would contain the "print" command. 

I think you have a good point about not "fearing" the command line, but I started with DOS 3.0 when all there was was a command line. I don't fear it. I want to see Linux have one missing feature. By the way, the Gats version of an OS can't print the files in a directory either. I think this was his way of preventing people from locating files buried deep within sub-sub directories and hoping amateurs would give up on "hacking" his stuff. Didn't happen by the bye.

---

### Post by bruce89 on 2008-10-07
> **Mark_in_Hollywood said:**
> At one time, before Linux, I had (I won't mention the OS name), Word Perfect. Now that company sold an add-on called Word Perfect Library. And if you wanted to print all the files in a directory, all you had to do was click the File Menu and pull the bar down to the "print".

```
<?xml version="1.0"?>
<interface>
  <object class="GtkUIManager" id="uiman">
    <child>
      <object class="GtkActionGroup" id="actions">
        <child>
          <object class="GtkAction" id="file-menu">
            <property name="name">FileMenu</property>
            <property name="label" translatable="yes">_File</property>
          </object>
        </child>
        <child>
          <object class="GtkAction" id="print">
            <property name="name">Print</property>
            <property name="stock_id">gtk-print</property>
          </object>
        </child>
      </object>
    </child>
    <ui>
      <menubar name="menubar">
        <menu action="file-menu" name="file-menu">
        </menu>
      </menubar>
    </ui>
  </object>
  <object class="GtkWindow" id="window">
    <property name="title">Print</property>
    <property name="icon-name">print</property>
    <signal handler="gtk_main_quit" name="destroy"/>
    <child>
      <object class="GtkVBox" id="vbox">
        <child>
          <object class="GtkMenuBar" id="menubar" constructor="uiman"/>
            <packing>
              <property name="expand">False</property>
            </packing>
        </child>
      </object>
    </child>
  </object>
</interface>
```

---

### Post by koenn on 2008-10-09
> **Mark_in_Hollywood said:**
> How does that print all the files in a directory when there are more files than can be displayed on screen at one time?
it doesn't, obviously. It illustrates the shortcomings of a GUI environment

For jobs like this, the shell has the advantage that it's already text-based so you can just do your listing and print it, or filter/sort it, dump it in a file, copy and paste from it, open it in OOo and save it as odt, etc.
It's rather typical for Unix to have all these tools and let the user combine them (if necessary, create a script with a desktop launcher to do it), in stead of what you propose: a single tool that does everything. 
Like with ". I want to print it to a piece of paper or to an .odt file ... neatly formatted for the 8 1/2 X 11 inch page".
Your tool would be useless on systems without OOo. It would also be useless to users who want their output in another document format than odt. It would be just as useless for every user that doesn't use US Letter as standard paper size.  Or it would need to have a list of configurable options so the user can decide what document type the output should be, what paper size to format for, and so on. 

I'm not saying it's such a terrible idea, just that it has the potential of becoming a monstrosity, while a simple "ls > textfile" can do the job.
On the other hand, it might just be the kind of thing the Gnome devs like ...

---

### Post by fjf on 2008-10-09
I had that problem once, and got here the answer:  ls |lpr

---

