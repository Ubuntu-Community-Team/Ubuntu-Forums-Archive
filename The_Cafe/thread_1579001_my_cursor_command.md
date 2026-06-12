---
title: "my cursor command"
date: 2010-09-21
forum: The Cafe
---

### Post by searchfgold6789 on 2010-09-21
Here is my command to get all the cursors for ubuntu.
To get the cursors:
```
sudo apt-get install libxcursor1 oxygen-cursor-theme oxygen-cursor-theme-extra dmz-cursor-theme xcursor-themes chameleon-cursor-theme crystalcursors
```
After you get the cursors, you must run the following command to set the default system cursor theme:
```
sudo update-alternatives --config x-cursor-theme
```Look through the list to find the cursor you want the system to use ( usually DMV ), type in the number you want and that will be the cursor your system will use i.e. before you login. Setting this back to normal is strongly suggested especially for computers that have multiple users to prevent torturous questioning.
Setting your cursor theme for after you login varies from distribution to distribution:

[LIST]
[*]Ubuntu: System > Preferences > Appearance
[*]Kubuntu: System Settings > Keyboard and Mouse > Mouse > Cursor Theme
[*]Xubuntu: Applications > Settings > Xfce 4 Settings Manager > Mouse
[*]Others: Please post here and I will add :)
[/LIST]
Enjoy. More cursors coming soon.

---

