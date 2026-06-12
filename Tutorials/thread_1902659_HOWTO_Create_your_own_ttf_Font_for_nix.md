---
title: "HOWTO: Create your own ttf Font for *nix"
date: 2011-12-31
forum: Tutorials
---

### Post by lkraemer on 2011-12-31
I wanted to install a new font in my *nix system (Debian 6 - SQUEEZE) and
I also was helping my brother recreate an old DOS Font that was being used
in a small 486 Single Board Controller to send messages to LED & LCD Controllers
that had several pushbuttons, and built in LED or LCD displays for messages.
The 486 DOS Single Board was not being produced, and was being replaced by a
newer Single Board Computer.  The new SBC would be required to display the exact
same messages in the exact same font............WHOO HOO!!  How are we going to
do this in *nix, because the Original Character set was using the Borland BGI
Library to write the Font directly to the Display?

A search of the Internet found this BLOG:
[http://stackoverflow.com/questions/3750124/how-to-convert-a-bitmap-font-fon-into-a-truetype-font-ttf](http://stackoverflow.com/questions/3750124/how-to-convert-a-bitmap-font-fon-into-a-truetype-font-ttf)
but, it didn't quite work the way I expected.  So, I conjured up my own method.
It is detailed below.  Maybe it will give you the assist you need.


**SOFTWARE TO BE PRE-INSTALLED:**

1.  Autotrace-0.31.1  -- SourceForge Download - used with FontForge
      ```

      gunzip autotrace-0.31.1.tar.gz
      tar xf autotrace-0.31.1.tar
      cd autotrace-0.31.1
      ./configure
      make
      sudo make install
      
```
2.  FontForge  -- via Synaptic Package Manager
3.  gbdfed  -- via Synaptic Package Manager
4.  MSPaint in WINE  
REF: [http://ubuntuforums.org/showthread.php?t=660408&highlight=MSPaint&page=3](http://ubuntuforums.org/showthread.php?t=660408&highlight=MSPaint&page=3)
Posting #30
5.  Codeweavers Crossover 9 Pro -- To allow Installing Font Editor in a Bottle and execute Font Editor
6.  SIB Font Editor  -- Internet Download 30 Day trial Windows Software



The first thing to be done was to EXTRACT the FONT.fnt file from the Controller, and either decode the file, or display it's contents.


1.  Copy the Controller.EXE, FONT.fnt, EGAVGA.BGI files to *nix DOS Subdirectory
    ie.  ~/386_C/CDR/TC/UFC.EXE
    (The source was modified to lock up in a loop, displaying the Initial Character set on my Laptop display
     using the original FONT.fnt file.  No file decoding was necessary.  This saved hours....)

2.  In *nix run DOSBox, and mount the DOS Subdirectory. (mount c ~/386_C/CDR/TC on my system)

3.  Set the *nix Computer's Video to 800x600 mode, so the Characters will be as large as possible on the display.

4.  Run Controller.EXE from DOSBox so the Graphics are displayed on the screen in 800x600, and remain there so we can capture them.

5.  Use *nix to screen capture the Characters to a UFCFont.png file. (BMP not available in ScreenCapture)

6.  Open the UFCFont.png file with MSPaint (in *nix) and ZOOM to 800X, then Invert the colors.

7.  Save the file as UFCFontI.BMP. (~/Desktop/UFCFontI.bmp)

8.  Crop the file in *nix using Gimp, then resave. (~/Desktop/UFCFontI.bmp)

9.  Copy ~/Desktop/UFCFontI.bmp to ~/Desktop/UFCFontIR.bmp and use the image to create a Water Level Line
    along with determining the Number of Pixels required to create a box size that can contain each possible
    Character such that it is positioned exactly the same as we scroll through the characters.
   
10. Once a box size is determined, mine was 12x60 Pixels, copy each character into a box of that size, in a
    second window also running MSPaint.

11. Save each character as 0x20.bmp, 0x22.bmp, 0x23.bmp.......

12. Install SIB Font Editor (Win Program) in *nix, in a Bottle named (SIB_FE) in Codeweavers Crossover 9 Pro.

13. Run Font_Editor and create the newDOS.fon.  Import each Character's BMP file.  Save the complete font file.

14. Install gbdfed in *nix and generate the newDOS.bdf file.  (FontForge wouldn't load this BDF file.......??,
    but there may be other Font Software that will/can use it.  Used as a backup for a possible parallel method
    that wasn't used....)

15. Generate the newDOS.SFD file, and save the file

16. Start FontForge in *nix, and open a newDOS.fon font file.

17. Double Left Click on character 0x21 to open the editor.

18. File, Import /home/larry/bgi/FxxFonts/UFC_symbols/0x21.bmp

19. Element, Autotrace, Close Window.  Use autotrace parameters of: -corner-surround=1 -line-threshold=10
      The first Font Character is loaded.  I copied 0x21 to 0x20 and deleted the contents with CNTL Z.
      Close the Edit Window.  You can Right Click on a Character and DELETE it from the Font Window.
      If you load the wrong BMP file, just Load the new one over the Background BMP Image.

20. Repeat from Step #17 until all Characters through 0x7F are done.
      I had to edit one bmp for the 'a' to change one Pixel to White. (REF: 0x61a.bmp)
      I had to manually edit the Degree Character Inside Loop CCW, and Outer Loop CW, because of the intersecting lines.

21. Correct any char Errors manually, using mostly the function "Add a curve point".
    Activating View->Show->Almost Horizontal/Vertical Lines makes the work much easier.

22. Save the newDOS.SFC file for future edits.

23. Generate a True Type Font: File->Generate Fonts and choose truetype as format.  Here is where you will find any Character errors.

24. Window, New Metric to see what the spacing look s like and to correct the Left & Right Bearing from Metrics.
      Correct the spacing to ~230 versus 1000.

25. Select all the Imported Characters, Hold LEFT SHIFT & Left Click on Every Character in the Font, and Set Width
    to 230 in the Metric Window.

26. Export the newDOS.TTF File.

27. Install the newDOS.TTF file in Debian 6.
    (SEE REF's below on how to install a ttf font in *nix)

**REF - Additional Fonts:**
[http://www.dafont.com/](http://www.dafont.com/)
[B]
Extra Needed Info:[/B]
[http://www.linuxjournal.com/content/installing-fonts-linux](http://www.linuxjournal.com/content/installing-fonts-linux)
[http://wiki.debian.org/Fonts#Adding_fonts](http://wiki.debian.org/Fonts#Adding_fonts)
[http://linuxandfriends.com/2009/07/20/how-to-install-fonts-in-linux-ubuntu-debian/](http://linuxandfriends.com/2009/07/20/how-to-install-fonts-in-linux-ubuntu-debian/)

ZIT ZOT!

lk

---

