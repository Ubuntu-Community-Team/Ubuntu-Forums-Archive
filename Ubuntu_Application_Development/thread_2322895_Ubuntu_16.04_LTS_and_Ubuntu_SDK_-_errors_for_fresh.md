---
title: "Ubuntu 16.04 LTS and Ubuntu SDK - errors for fresh install of ubuntu sdk"
date: 2016-05-01
forum: Ubuntu Application Development
---

### Post by antonino-giannone on 2016-05-01
Hi, I started to study the development of Ubuntu for the mobile world. I write here what I did to install the development environment.
 [TABLE]
[TR]
[TD="class: votecell"]I hope someone can help me. Thanks to everyone![/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]

1. Fresh installation of Ubuntu 16.04 LTS Desktop
2. Update and upgrade it
3. In according to communication of Zoltán Balogh of 2016-April and 
    the installation guide of Ubuntu SDK, I followed this instructions sequence: 
        ```

sudo add-apt-repository ppa:ubuntu-sdk-team/ppa
sudo apt update && sudo apt install ubuntu-sdk
sudo apt update && sudo apt dist-upgrade
sudo apt install ubuntu-sdk-api-15.04-armhf
sudo apt update && sudo apt install ubuntu-sdk-ide ubuntu-sdk-dev
```

[https://lists.ubuntu.com/archives/ubuntu-devel/2016-April/039322.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-April/039322.html)

4. Well! I started to use IDE and I received the update notification of ubuntu-sdk-15.04-armhf kit. 
    I don't accepted the request update.

    At this time I have this content for armhf kit:
    ```
ls -l /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/Ubuntu/

    drwxr-xr-x 11 root root 4096 gen 22 20:29 Components
    drwxr-xr-x  2 root root 4096 gen 22 20:28 Content
    drwxr-xr-x  2 root root 4096 gen 22 20:30 DownloadManager
    drwxr-xr-x  2 root root 4096 gen 22 20:29 Layouts
    drwxr-xr-x  2 root root 4096 gen 22 20:28 MediaScanner.0.1
    drwxr-xr-x  3 root root 4096 gen 22 20:30 OnlineAccounts
    drwxr-xr-x  2 root root 4096 gen 22 20:29 PerformanceMetrics
    drwxr-xr-x  2 root root 4096 gen 22 20:30 PushNotifications
    drwxr-xr-x  2 root root 4096 gen 22 20:28 SyncMonitor
    drwxr-xr-x  3 root root 4096 gen 22 20:29 Telephony
    drwxr-xr-x  2 root root 4096 gen 22 20:29 Test
    drwxr-xr-x  3 root root 4096 gen 22 20:29 Unity
```

5. I created my first project from this template: QML App with Simple UI(qmake) 
    (QtQuick2 app with kit using 15.04 click root)

    There is an error on Main.qml for import Ubuntu.Components 1.3

    ```
[11:58:52] ii click-reviewers-tools 0.42

    Warnings while parsing QML type information of /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/Ubuntu/Components:
    Failed to parse "/var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/Ubuntu/Components/plugins.qmltypes".
    Error: /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/Ubuntu/Components/plugins.qmltypes:1443:39: Meta object revision without matching export.
    /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/Ubuntu/Components/plugins.qmltypes:1452:39: Meta object revision without matching export.
    /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/Ubuntu/Components/plugins.qmltypes:1470:39: Meta object revision without matching export.

    Warnings while parsing QML type information of /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/QtMultimedia:
    Failed to parse "/var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/QtMultimedia/plugins.qmltypes".
    Error: /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/QtMultimedia/plugins.qmltypes:0:0: Expected a single import.

```
6. Ok, I close ide and reopen it. 
    Well, I accept request update for kits: ubuntu-sdk-15.04-armhf and ubuntu-sdk-15.04-i386

    Now I have this content for amrhf kit

    ```
ls -l /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml/Ubuntu/

    drwxr-xr-x 2 root root 4096 mag  1 12:16 Content
    drwxr-xr-x 2 root root 4096 mag  1 12:16 DownloadManager
    drwxr-xr-x 2 root root 4096 mag  1 12:16 Layouts
    drwxr-xr-x 2 root root 4096 mag  1 12:16 MediaScanner.0.1
    drwxr-xr-x 3 root root 4096 gen 22 20:30 OnlineAccounts
    drwxr-xr-x 2 root root 4096 mag  1 12:16 PerformanceMetrics
    drwxr-xr-x 2 root root 4096 mag  1 12:16 SyncMonitor
    drwxr-xr-x 3 root root 4096 gen 22 20:29 Unity
```

    The following folders have been deleted after the update request---is it correct?
    ```
drwxr-xr-x 11 root root 4096 gen 22 20:29 Components
    drwxr-xr-x  2 root root 4096 gen 22 20:30 PushNotifications
    drwxr-xr-x  3 root root 4096 gen 22 20:29 Telephony
    drwxr-xr-x  2 root root 4096 gen 22 20:29 Test
```


7. Now I have this error on import Ubuntu.Components 1.3:

    ```
QML module not found
    import paths /var/lib/schroot/chroots/click-ubuntu-sdk-15.04-armhf/usr/lib/arm-linux-gnueabihf/qt5/qml
    For cmake project use QML_IMPORT_PATH variable to add import paths
```


8. My qtchooser and qmake version command output:

    ```
qtchooser -l
    4
    5
    default
    qt4-x86_64-linux-gnu
    qt4
    qt5-x86_64-linux-gnu
    qt5
    --------
    --------
    qmake -version
    QMake version 3.0
    Using Qt version 5.5.1 in /usr/lib/x86_64-linux-gnu
```

---

