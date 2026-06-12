---
title: "How to Install Microsoft Text Fonts in Ubuntu Linux"
date: 2009-02-08
forum: The Cafe
---

### Post by guriman on 2009-02-08
Arial, Times New Roman, Impact and Verdana are some of the most commonly used fonts. They are so widely used in fact that whenever you open a Word document from any computer, you immediately expect to find their presence. However, on your newly installed Ubuntu (and many other Linux distros), you will find that there is absolutely no trace of any of these font

Ubuntu, by default, does not include the commonly used Microsoft core fonts in its installation. The set of fonts that it uses is not supported in Windows or Mac. This means that if you create a document and send to your partner for editing, he/she will not be able to view it in the way that it was originally formatted. Vice versa, you won&#8217;t be able to view the document that your friend sends you in the way that it was formatted, unless he/she is using the same fonts as you.

Luckily, installing the Microsoft core fonts package (and any other new fonts) in Ubuntu is easy. Here&#8217;s how you can do it on your own:

[B]Installing Microsoft Core Fonts in Ubuntu Linux
[/B]
The Microsoft core fonts package consists of the following fonts:

      * Andale Mono
      * Arial Black
      * Arial (Bold, Italic, Bold Italic)
      * Comic Sans MS (Bold)
      * Courier New (Bold, Italic, Bold Italic)
      * Georgia (Bold, Italic, Bold Italic)
      * Impact
      * Times New Roman (Bold, Italic, Bold Italic)
      * Trebuchet (Bold, Italic, Bold Italic)
      * Verdana (Bold, Italic, Bold Italic)
      * Webdings

To install them, open up your Synaptic Package Manager (System -> Administration -> Synaptic Package Manager). Scroll down till you find msttcorefonts. Check the box beside it and select Mark for Installation. Click Apply at the menubar to install the fonts package.

Alternatively, if you prefer the terminal way, simply type the following command in your terminal.

sudo apt-get install msttcorefonts

**Installing new fonts**

Installing the Microsoft core fonts package is only the beginning. There will be many occasions where you need to install a new set of fonts for a specific project. Here is how you can do it :

If you are installing the new fonts for personal use and do not want others to have access to them, simply create a .fonts folder in your Home directory and paste all the fonts into it. Here&#8217;s the steps:

    * 1. Download the fonts (it should be in zipped format)
    * 2. Extract the fonts.
    * 3. Open nautilus (Places -> Home). Press Ctrl + H to reveal all the hidden files and folders.
    * 4. Check if the .fonts folder exist. If not, create the folder and name it .fonts.
    * 5. Copy and paste the new font(s) into the .fonts folder.
    * 6. Restart your application. The fonts should be available for your use now.

If you want to install system-wide and allow others to use it:

    * 1. Create a new folder in your Desktop. Name it newfonts
    * 2. Download the new font(s) and extract to the newfonts folder
    * 3. Open a terminal
    * 4. Key in the command: sudo cp -R ~/Desktop/newfonts /usr/share/fonts. This will copy your new font(s) to the system font folder.
    * 5. Restart your application. The new fonts are now available for system-wide use.

If you are using KDE, there is a font installer application that allows you to install new fonts easily.The Font Installer application is found under System Settings.

**Better Font Rendering**

Now that you have installed your favorite fonts in your system, here&#8217;s a simple trick to improve the font rendering and make it look nicer.

Open up your Appearance configuration page (System -> Preferences -> Appearance)

Click on the Fonts tab. Under the Rendering section, check on the subpixel smoothing button.

You should notice the differences immediately.

If you are using Ubuntu 8.04 or an earlier version, this is what you need to do:

Type in the following command in the terminal

sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/

Logout and login again. You should see a noticeable difference in the font rendering.

---

### Post by SunnyRabbiera on 2009-02-08
Or, just install the MS corefonts from the ubuntu repositories :D
The only other issue one might face in ubuntu is that gnome has no decent font installer, I mean I know its as easy as creating a folder named .fonts but I wish there were a more upfront way to do it.

---

### Post by phrostbyte on 2009-02-08
[Or you can just click here]("apt://msttcorefonts")


:p:KS

Edit: also, there is this [font set,]("apt://ttf-liberation") which has the same size/width as MS fonts, but is 100% FOSS. I think they look better and use them for my desktop and printing.

---

