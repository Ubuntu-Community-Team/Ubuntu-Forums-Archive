---
title: "Procedure to install iTunes in Wine on Ubuntu"
date: 2011-02-15
forum: Wine
---

### Post by arancher on 2011-02-15
1. This Procedure is to provide a Step-by-Step process on how I got
    these products to work up to the point of bringing up iTunes
    under wine and connecting successfully to the iTune store.

    Also please be aware that this install procedure was based on a
    huge amount of trial-and-error on my part and the result of
    gathering a large number of peoples suggestions and experience
    from their individual attempts to get this to work.
    I would be happy to give them all credit for their parts in this
    project if I could remember all of them.

 2. My system
    Intel  - Core 2 Duo - 1 Gb Ram
    Ubuntu - Lucid Lynx 10.04
    Kernel - 2.6.32

 3. Research
    I went to WineHQ.com -> AppDB -> CLick on Browse Apps on left side ->
                  Name Contains itunes
                 Click on itunes
    Read the writeup of the tests done using various configurations.
    I choose the SILVER example using iTunes 10.1.1 WITH wine 1.3.10
 
4. Packages used
    1. Wine             1.3.11
    2. iTunes         10.1.1
    3. QuickTime     7.6.9
    4. Microsoft Visual C++ 2005 Service Pack 1 Redistributable Package
          ATL Security Update

 5. Download the Packages needed
     1. In order to be able to get the latest Development versions of WINE
             go to these instructions:
          1. winehq.org/download
          2. click Download Ubuntu Packages
          3. follow the directions for adding "the WineHQ PPA Repository"
             These instructions tell you to do the following:
                From the Desktop -> Click Applications  ->
                   -> Ubuntu Software Center -> Edit ->
                   -> Software Sources -> Other Software tab
                   -> Add -> ppa:ubuntu-wine/ppa
                   -> Click "Add Source"
                   -> Then Close out
          4. after the above step is completed do the following:
                System -> Administration -> Synaptic Package Manager ->
                       -> search for wine -> select "wine 1.3" currently 1.3.11
                           and install it along with all the associated programs
          5. Also in Synaptic install the product "ubuntu-restricted-extras"
                   and all its associated programs
      2. Now download iTunes - I got it from oldapps.com
            oldapps.com -> Audio Utilities -> iTunes -> Itunes 10.1.1  (78.08 Mb)
            file is "iTunesSetup1011.exe"
      3. Now to download QuickTime - I got this from Apple
            apple.com/quicktime/download
            QuickTime  7.6.9 for XP  -> Download now
            file is QuickTimeInstaller.exe
      4. Now download the "Microsoft Visual C++ 2005 Service Pack 1
                                            Redistributable Package
                                            ATL Security Update"
         go to microsoft.com/downloads/en
             search for "ATL security update"
             Click on the file
             download the file vcredist_x86.exe (2.6 Mb)
      5. Place all the Downloaded files in your $HOME Directory

 6. Preliminary preperation
     In order to get rid af any left over Wine configuration, do the following
       commands in a Terminal session.  This were taken from:
              wiki.winehq.org/FAQ
              item 5.2 - How do I uninstall *all* windows applications?
      rm -r $HOME/.wine
      rm    $HOME/.config/menus/applications-merged/wine*
      rm -r $HOME/.local/share/applications/wine
      rm    $HOME/.local/share/desktop-directories/wine*
      rm    $HOME/.local/share/icons/????.*.{xpm.png}
      rm    $HOME/.local/share/icons*-x-wine-*.{xpm.png}

 7.  start the install procedure
      Do all of these Steps in a terminal session
      This is to Initialize the Wine System
      winecfg
         Application tab  ->  Windows version -> Windows XP
         Drives        tab  ->  Autodetect
         Audio         tab  ->  Alsa dvirer -> Checked
                                       OSS driver -> Unchecked
                                       test Sound -> got a beep
         Graphic      tab  ->  Emulate a virtual Desktop
                                       1024 x 768
                                       Direct3D - Vertex Shader - none
                                       Unclick - Allow Pixel Shader
      Apply -> OK

 8. Now install the Visual C++ 2005 Service Pack Update
     wine vcredist_x86.exe
         accept the License -> Yes

 9. Now install itunes
    wine iTunesSetup1011.exe
          Welcome                                    -> Next
          Important note regarding Ping    -> I Accept  -> Next
          Un-click the (3) Boxes                 -> Install
          AutoRun is turned OFF                 -> NO
          Window may go Black                 -> Ignore it
          Congratulations
             iTunes has been successfully installed on your Computer
          Uncheck the Open iTunes box      -> Finish
     If it dosn't end properly   -> Set Focus on the Terminal screen ->
                                -> CTRL+C to end it.

10. Now remove QuickTime
     wine uninstaller -> Click QuickTime -> Remove button
               REMOVE button ->
               Completely Remove -> Yes
               QuickTime Installer Completed -> Finish -> O.K.
    If it dosn't end properly   -> Set Focus on the Terminal screen ->
                                -> CTRL+C to end it.

11. Now Install QuickTime
      wine QuickTimeInstaller.exe
          REPAIR Button
          QuickTime has been successfully installed on your Computer
          Finish
     If it dosen't end properly  -> Set Focus on the Terminal screen ->
                                 -> CTRL+C to end it.

12. Now install mdac_typ.exe
      winetricks   -> go to mdac25    -> select it  -> OK
         Accept License                      -> Yes         -> Next
        Installing the Software           -> Next       -> Finish

13. In order to run iTunes, issue the following command:
      wine ".wine/drive_c/Program Files/iTunes/iTunes.exe"
      When running the first time, you will get some additional messages
          Welcome to iTunes                                               -> Next
          Find Media Files                                 -> Unclick    -> Next
          Keep Tunes Media Folder Organized    -> No          -> Next
          Download Album Artwork                                      -> Next
          Warning about CD's
             I ignored it                                                         -> Finish
       A new version of iTunes is available                  -> Don't Download
       You will probably have to do a CTRL+C to end it.

14. The Product is now running, for better or Worse.
      I know nothing more about its usefulness or usability beyond this point.

Conclusion:
I hope this procedure will be of use to some people in getting this
facilty to work on a Linux System.
As an aside, I only have a 56K Internet connection.
For those of you with faster connections, the product may work a lot better.

Yours truly,
Frank Krauss

---

### Post by marin123 on 2011-02-15
but you cannot sync music to an ipod, right?

---

### Post by searchfgold6789 on 2011-02-15
A good guide, thank you for that.
But I would like to know if your method will solve the issue many people have, with not being able to connect to their iPod with iTunes under Wine.

---

### Post by marin123 on 2011-02-15
> **searchfgold6789 said:**
> A good guide, thank you for that.
But I would like to know if your method will solve the issue many people have, with not being able to connect to their iPod with iTunes under Wine.

wait for wine 1.4. wine doesnt support usb for now.
there are ways to patch and build wine with usb support but i couldnt manage to get my program to recognize my usb flash drive.

---

### Post by searchfgold6789 on 2011-02-15
OK, thanks for clearing that up!

---

### Post by AHoneybun on 2011-02-22
So any news on the new Wine working with iTunes to sync music to a Apple device?

---

### Post by theou huios on 2011-02-22
thanks :D

---

