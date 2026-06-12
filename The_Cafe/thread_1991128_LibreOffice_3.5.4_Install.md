---
title: "LibreOffice 3.5.4 Install"
date: 2012-05-30
forum: The Cafe
---

### Post by scouser73 on 2012-05-30
**Enter the following commands into the Terminal one at a time, pressing enter after each command is copy and pasted.**

1 ```
sudo apt-get remove libreoffice*.*
```

*If you have OpenOffice installed and would like to remove it and install LibreOffice then the Terminal command is;*

```
sudo apt-get remove openoffice*.*
```

2 Download LibreOffice **(Remember that you need the .deb version **NOT** RPM)**

3 Extract LibreOffice to *~/Desktop*

4 Rename the extracted file as ```
libreoffice
```

5 ```
sudo dpkg -i ~/Desktop/libreoffice/DEBS/*.deb
```

6 ```
sudo dpkg -i ~/Desktop/libreoffice/DEBS/desktop-integration/libreoffice3.5-debian-menus_3.5.4-2_all.deb
```

Installing a Language Pack for your locale

Download the relevant Language Pack for your needs **(Remember that you need the .deb version **NOT** RPM)**

1 Save it to *~/Desktop*

2 Extract the downloaded file

3 Rename the extracted file as ```
libreoffice
```

Enter the following command into Terminal

4 ```
sudo dpkg -i ~/Desktop/libreoffice/DEBS/*.deb
```

---

