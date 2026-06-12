---
title: "Run Mozilla Firefox Stable, Firefox Nightly and Firefox Developer Edition sidebyside"
date: 2017-11-12
forum: Tutorials
---

### Post by thehannibal on 2017-11-12
I spent Two Weeks trying to solve the mystery of running 3-editions of Firefox at once. I solved it finally and wanted to share this with you :

  Here are screenshots of 3-firefox running side-by-side :

Stable: [https://uploads.disquscdn.com/images/c7a297d655804d3faab1a87892aa9861193217d607c2b2baa17f7fb03dee34c8.png](https://uploads.disquscdn.com/images/c7a297d655804d3faab1a87892aa9861193217d607c2b2baa17f7fb03dee34c8.png)

Dev: [https://uploads.disquscdn.com/images/e96355fa4b399c394ff9eeec2e5743c10bff3a9971216c9d04f1ea757f1d4e95.png](https://uploads.disquscdn.com/images/e96355fa4b399c394ff9eeec2e5743c10bff3a9971216c9d04f1ea757f1d4e95.png)

Nightly: [https://uploads.disquscdn.com/images/30f422aaa8ac020167e0e4e67a906fac4055fef509dab475c14b5b5acd5a6213.png](https://uploads.disquscdn.com/images/30f422aaa8ac020167e0e4e67a906fac4055fef509dab475c14b5b5acd5a6213.png)

   How to do this ?

1> Stable: It will be come pre-installed in most Linux Distro's and no need to install it if it's not already available install it using ```
sudo apt install firefox
```

2> Developer Edition: Go ahead to this site and download the .tar.bz2 [https://www.mozilla.org/en-US/firefox/developer/](https://www.mozilla.org/en-US/firefox/developer/) 
                                     Now go to the downloads folder and extract the tar ```
tar xvjf name.tar.bz2
```
                                Go into the extracted folder ```
cd firefox*
```
                                Run firefox-dev ```
./firefox
```
                                By default firefox developers edition uses a differnt profile so no need to alter anything.
                                Download a cool icon for Firefox Developer Edition Place it inside firefox folder which was downloaded
                                Create a .desktop file for Quick-launch
                               
firefox-dev.desktop
```

[Desktop Entry]
Name=Firefox Developer 
GenericName=Firefox Developer Edition
Exec=/home/username/Downloads/firefox-dev/firefox
Terminal=false
Icon=/home/username/Downloads/firefox-dev/iconname.png
Type=Application
Categories=Application;Network;X-Developer;
Comment=Firefox Developer Edition Web Browser
                               
                               
``` 
                               Place .desktop file that you created in this path
                                ```
/home/username/.local/share/applications
```
And now your unity search will show firefox-dev edition and you can go ahead and open it and pin it to launcher.

3> Nightly: Use to add nightly ppa repo 

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```
                 ```
sudo apt-get update
```
                 ```
sudo apt install firefox-trunk
```
                 Nightly will be installed with a different profile and location than firefox-stable and you can use both side-by-side

---

