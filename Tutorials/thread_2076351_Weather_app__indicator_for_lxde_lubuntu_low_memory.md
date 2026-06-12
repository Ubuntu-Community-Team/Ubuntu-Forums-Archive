---
title: "Weather app / indicator for lxde lubuntu low memory  also provides volume settings"
date: 2012-10-25
forum: Tutorials
---

### Post by ronniew on 2012-10-25
I will try to keep this thread updated for this super simple solution for desktop weather & forecasts for anyone running lxde lubuntu or just want a lightweight virtually no memory solution to one click weather for your os.

First for Lubuntu I always stick with the LTS release.. Although there hasn't been an official one yet 12.04 is the defacto LTS release for Lubuntu.

That being said if your running 12.10 your instructions will be slightly different but not much... 

**These instructions actually provide two solutions,** the installation of xterm which is required actually fixes the default volume settings when selected from the volume icon in the panel.. screenshot attached... no more need for pavcontrol or gnome-mixer. _When you right click on the volume icon in Lubuntu and select volume settings alsamixer will be open within an xterm window._

Now onto getting the weather app/indicator working.

Here is everything that needs to be installed first.
Open your terminal and enter the following lines.

**Lubuntu 12.10 Instructions**
sudo apt-get install xterm
sudo apt-get install weather-util
sudo apt-get install weather-util-data
[B]
For Lubuntu 12.04 Instructions[/B]
sudo apt-get install xterm
Click to download & install [weather-util]("http://mirror.pnl.gov/ubuntu//pool/universe/w/weather-util/weather-util_2.0-1_all.deb")
Click to download & install [weather-util-data]("http://mirror.pnl.gov/ubuntu//pool/universe/w/weather-util/weather-util-data_2.0-1_all.deb")

Once installed we are really close to being done

Next is to create a desktop icon that we will place in the usr/share/applications folder.

To create a desktop icon right click on the desktop and create a blank file. Name the file whatever you want just end it with .desktop    I usually name the icon fastforecast.desktop

Once the file is created right click on it and open it with leafpad.

Copy and paste the following code in it

```
[Desktop Entry]
Version=1.0
Name=Fast Forecast
Comment=Quick xterm weather launcher.
Exec=xterm -bg SteelBlue4 -fg white -geometry 75x45 -hold -e weather --forecast --alert --no-cache-data ZIPCODE
Terminal=false
Type=Application
Categories=Utility;
Icon=xfce4-weather
```

Once copied replace the "ZIPCODE" with your actual zip code. Then close and save... 

Now you can move the icon to your usr/share/applications folder a number of different ways. But to do it from the command line is fairly simple.

I'll assume you created the new file on your desktop, if so move it to the correct folder using the following commmands. 

Open your terminal, 

cd Desktop
sudo mv fastforecast.desktop /usr/share/applications

enter your password and the icon should disappear from your desktop

Now you should see it appear in your accessories menu. You can access it from there..

For lxde / lubuntu users you can then right click on the panel and select add remove panel items, click on add and add an application launch bar.

place it where ever you like on your panel,,, then right click on it and select the fastforecast weather icon that is now located in your accessories menu..

and there you have it,, now you have access to weather without using any memory until you click on it.

remember that volume settings on the volume icon will also work now thanks to the installation of xterm at the beginning... screenshot below.

[IMG]http://www.unleashpc.com/weatherandvolume.png[/IMG]

Alternatively you can also set you own custom color by replacing the color names using the chart provide at the following website..

[Click for Xterm Colors]("http://critical.ch/xterm/")

You can also set your own fonts by using xfontsel in the terminal and replacing the appropriate line in the .desktop file with what you like using xfontsel.

Below is an alternate desktop icon file with fonts predetermind.

```
[Desktop Entry]
Version=1.0
Name=Fast Forecast
Comment=Quick xterm weather launcher.
Exec=xterm -fn -misc-fixed-medium-r-*-*-13-*-*-*-*-*-*-* -bg SteelBlue4 -fg white -geometry 75x45 -hold -e weather --forecast --alert --no-cache-data 17403
Terminal=false
Type=Application
Categories=Utility;
Icon=xfce4-weather
```

Nice simple solution for no memory waste junkies like myself :)

*****
I applied a quick update to both sets of codes above, fast forecast will now include localweather alerts.. If you applied this mod early please update.
*****

**I will be providing a series of easy solutions and linking to them below**
[lxde wallpaper changer]("http://ubuntuforums.org/showthread.php?t=2076417")
[aero snap for lubuntu]("http://ubuntuforums.org/showthread.php?p=12318519")
[expose feature for lubuntu]("http://ubuntuforums.org/showthread.php?p=12318587")

---

### Post by Farinet on 2012-10-26
Would that also work with European weather?

---

### Post by ronniew on 2012-10-26
I believe it queries the National Weather Service of the US only.

---

### Post by _6i on 2013-01-06
It works with both GPS co-ordinates and place/city names (searches for the nearest weather information in the database to the given location in a cca. 600km raduis, iirc) even for European cities.
However, it complains to me that there is no specified URL if I try to do a "--forecast" or "--alert" (using default settings – I didn't set up anything, just ran "weather <gps_co-ordinates_copied_from_google_maps>" in a terminal).

Read the "weather" or "weather-util" manual page.

---

### Post by netipot on 2013-01-12
I tried out your weather app mainly because my volume settings don't work.
I have lubuntu 12.10 installed on a T60 thinkpad & an old motion computing 1600 tablet. The first time I clicked on the volume settings I got alsamixer on both machines after installing lubuntu, but thereafter never again. What happens now is nothing except a new and ineffective sound applet appears in the systems tray.
After following your procedure there was no change.  All that happens is that it opens another volume app in my systems tray that I can only get rid of by logging out. I can manage my sound by typing "alsamixer" in terminal.
On the bright side I do have a really cool weather app. I do not like the icon associated with it however. Is there a way of replacing the icon?

---

