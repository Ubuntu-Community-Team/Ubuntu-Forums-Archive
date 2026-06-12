---
title: "I am not able to login after locking screen"
date: 2023-02-07
forum: Ubuntu, Linux and OS Chat
---

### Post by ishackigozi on 2023-02-07
We are using a gnome-session and launching it using export XDG_SESSION_TYPE=x11; /usr/bin/gnome-session. I am able to launch it, but after I lock the screen or the screen times out, I am not able to log back into the desktop. When I enter the password, the screen freezes. This is happening on Ubuntu 22.04.1

dpkg -l | grep gnome
ii  gir1.2-gnomebluetooth-3.0:amd64            42.0-5                                  amd64        Introspection data for GnomeBluetooth
ii  gir1.2-gnomedesktop-3.0:amd64              42.5-0ubuntu1                           amd64        Introspection data for GnomeDesktop (                                                                                                                                         GTK 3)
ii  gkbd-capplet                               3.26.1-2                                amd64        GNOME control center tools for libgno                                                                                                                                         mekbd
ii  gnome-accessibility-themes                 3.28-1ubuntu3                           all          High Contrast GTK+ 2 theme and icons
ii  gnome-bluetooth                            3.34.5-8                                amd64        GNOME Bluetooth Send To app
ii  gnome-bluetooth-3-common                   42.0-5                                  all          GNOME Bluetooth 3 common files
ii  gnome-bluetooth-common                     3.34.5-8                                all          GNOME Bluetooth common files
ii  gnome-calculator                           1:41.1-2ubuntu2                         amd64        GNOME desktop calculator
ii  gnome-calendar                             41.2-3                                  amd64        Calendar application for GNOME
ii  gnome-characters                           41.0-4                                  amd64        character map application
ii  gnome-control-center                       1:41.7-0ubuntu0.22.04.6                 amd64        utilities to configure the GNOME desk                                                                                                                                         top
ii  gnome-control-center-data                  1:41.7-0ubuntu0.22.04.6                 all          configuration applets for GNOME - dat                                                                                                                                         a files
ii  gnome-control-center-faces                 1:41.7-0ubuntu0.22.04.6                 all          utilities to configure the GNOME desk                                                                                                                                         top - faces images
ii  gnome-desktop3-data                        42.5-0ubuntu1                           all          Common files for GNOME desktop apps
ii  gnome-disk-utility                         42.0-1ubuntu1                           amd64        manage and configure disk drives and                                                                                                                                          media
ii  gnome-font-viewer                          41.0-2                                  amd64        font viewer for GNOME
ii  gnome-initial-setup                        42.0.1-1ubuntu2                         amd64        Initial GNOME system setup helper
ii  gnome-keyring                              40.0-3ubuntu3                           amd64        GNOME keyring services (daemon and to                                                                                                                                         ols)
ii  gnome-keyring-pkcs11:amd64                 40.0-3ubuntu3                           amd64        GNOME keyring module for the PKCS#11                                                                                                                                          module loading library
ii  gnome-logs                                 42.0-1                                  amd64        viewer for the systemd journal
ii  gnome-mahjongg                             1:3.38.3-2                              amd64        classic Eastern tile game for GNOME
ii  gnome-menus                                3.36.0-1ubuntu3                         amd64        GNOME implementation of the freedeskt                                                                                                                                         op menu specification
ii  gnome-mines                                1:40.1-1                                amd64        popular minesweeper puzzle game for G                                                                                                                                         NOME
ii  gnome-online-accounts                      3.44.0-1ubuntu1                         amd64        service to manage online accounts for                                                                                                                                          the GNOME desktop
ii  gnome-power-manager                        3.32.0-2build2                          amd64        power management tool for the GNOME d                                                                                                                                         esktop
ii  gnome-remote-desktop                       42.3-0ubuntu1                           amd64        Remote desktop daemon for GNOME using                                                                                                                                          PipeWire
ii  gnome-session-bin                          42.0-1ubuntu2                           amd64        GNOME Session Manager - Minimal runti                                                                                                                                         me
ii  gnome-session-canberra                     0.30-10ubuntu1                          amd64        GNOME session log in and log out soun                                                                                                                                         d events
ii  gnome-session-common                       42.0-1ubuntu2                           all          GNOME Session Manager - common files
ii  gnome-settings-daemon                      42.1-1ubuntu2.1                         amd64        daemon handling the GNOME session set                                                                                                                                         tings
ii  gnome-settings-daemon-common               42.1-1ubuntu2.1                         all          daemon handling the GNOME session set                                                                                                                                         tings - common files
ii  gnome-shell                                42.5-0ubuntu1                           amd64        graphical shell for the GNOME desktop
ii  gnome-shell-common                         42.5-0ubuntu1                           all          common files for the GNOME graphical                                                                                                                                          shell
ii  gnome-shell-extension-appindicator         42-2~fakesync1                          all          AppIndicator, KStatusNotifierItem and                                                                                                                                          tray support for GNOME Shell
ii  gnome-shell-extension-desktop-icons-ng     43-2ubuntu1                             all          desktop icon support for GNOME Shell
ii  gnome-shell-extension-ubuntu-dock          72~ubuntu5.22.04.1                      all          Ubuntu Dock for GNOME Shell
ii  gnome-startup-applications                 42.0-1ubuntu2                           amd64        Startup Applications manager for GNOM                                                                                                                                         E
ii  gnome-sudoku                               1:42.0-1                                amd64        Sudoku puzzle game for GNOME
ii  gnome-system-monitor                       42.0-1                                  amd64        Process viewer and system resource mo                                                                                                                                         nitor for GNOME
ii  gnome-terminal                             3.44.0-1ubuntu1                         amd64        GNOME terminal emulator application
ii  gnome-terminal-data                        3.44.0-1ubuntu1                         all          Data files for the GNOME terminal emu                                                                                                                                         lator
ii  gnome-themes-extra:amd64                   3.28-1ubuntu3                           amd64        Adwaita GTK+ 2 theme — engine
ii  gnome-themes-extra-data                    3.28-1ubuntu3                           all          Adwaita GTK+ 2 theme — common files
ii  gnome-todo                                 3.28.1-6ubuntu1                         amd64        minimalistic personal task manager de                                                                                                                                         signed to fit GNOME desktop
ii  gnome-todo-common                          3.28.1-6ubuntu1                         all          common files for GNOME To Do
ii  gnome-user-docs                            41.5-1ubuntu2                           all          GNOME Help
ii  gnome-video-effects                        0.5.0-1ubuntu1                          all          Collection of GStreamer effects
ii  language-pack-gnome-en                     1:22.04+20220721                        all          GNOME translation updates for languag                                                                                                                                         e English
ii  language-pack-gnome-en-base                1:22.04+20220721                        all          GNOME translations for language Engli                                                                                                                                         sh
ii  language-selector-gnome                    0.219.1                                 all          Language selector frontend for Ubuntu
ii  libgnome-autoar-0-0:amd64                  0.4.3-1                                 amd64        Archives integration support for GNOM                                                                                                                                         E
ii  libgnome-autoar-gtk-0-0:amd64              0.4.3-1                                 amd64        GTK+ widgets for the GNOME Autoar lib                                                                                                                                         rary
ii  libgnome-bg-4-1:amd64                      42.5-0ubuntu1                           amd64        Utility library for background images                                                                                                                                          - runtime files
ii  libgnome-bluetooth-3.0-13:amd64            42.0-5                                  amd64        GNOME Bluetooth 3 support library
ii  libgnome-bluetooth13:amd64                 3.34.5-8                                amd64        GNOME Bluetooth tools - support libra                                                                                                                                         ry
ii  libgnome-desktop-3-19:amd64                42.5-0ubuntu1                           amd64        Utility library for the GNOME desktop                                                                                                                                          - GTK 3 version
ii  libgnome-desktop-4-1:amd64                 42.5-0ubuntu1                           amd64        Utility library for the GNOME desktop                                                                                                                                          - runtime files
ii  libgnome-games-support-1-3:amd64           1.8.2-1build1                           amd64        library for common functions of GNOME                                                                                                                                          games
ii  libgnome-games-support-common              1.8.2-1build1                           all          library for common functions of GNOME                                                                                                                                          games (common files)
ii  libgnome-menu-3-0:amd64                    3.36.0-1ubuntu3                         amd64        GNOME implementation of the freedeskt                                                                                                                                         op menu specification
ii  libgnome-todo                              3.28.1-6ubuntu1                         amd64        library data for GNOME To Do
ii  libgnomekbd-common                         3.26.1-2                                all          GNOME library to manage keyboard conf                                                                                                                                         iguration - common files
ii  libgnomekbd8:amd64                         3.26.1-2                                amd64        GNOME library to manage keyboard conf                                                                                                                                         iguration - shared library
ii  libpam-gnome-keyring:amd64                 40.0-3ubuntu3                           amd64        PAM module to unlock the GNOME keyrin                                                                                                                                         g upon login
ii  libreoffice-gnome                          1:7.3.7-0ubuntu0.22.04.1                amd64        office productivity suite -- GNOME in                                                                                                                                         tegration
ii  libsoup-gnome2.4-1:amd64                   2.74.2-3                                amd64        HTTP library implementation in C -- G                                                                                                                                         NOME support library
ii  nautilus-extension-gnome-terminal          3.44.0-1ubuntu1                         amd64        GNOME terminal emulator application -                                                                                                                                          Nautilus extension
ii  network-manager-gnome                      1.24.0-1ubuntu3                         amd64        network management framework (GNOME f                                                                                                                                         rontend)
ii  network-manager-openvpn-gnome              1.8.18-1                                amd64        network management framework (OpenVPN                                                                                                                                          plugin GNOME GUI)
ii  network-manager-pptp-gnome                 1.2.10-1                                amd64        network management framework (PPTP pl                                                                                                                                         ugin GNOME GUI)
ii  pinentry-gnome3                            1.1.1-1build2                           amd64        GNOME 3 PIN or pass-phrase entry dial                                                                                                                                         og for GnuPG
ii  thunderbird-gnome-support                  1:102.4.2+build2-0ubuntu0.22.04.1       amd64        Email, RSS and newsgroup client - GNO                                                                                                                                         ME support
ii  xdg-desktop-portal-gnome                   42.1-0ubuntu1                           amd64        GNOME portal backend for xdg-desktop-                                                                                                                                         portal
ii  yaru-theme-gnome-shell                     22.04.4                                 all          Yaru GNOME Shell desktop theme from t                                                                                                                                         he Ubuntu Community
Feb  2 09:25:52 9000000741 gnome-session-binary[774754]: WARNING: App 'pulseaudio.desktop' exited with code 1
Feb  2 09:25:52 9000000741 dbus-daemon[774758]: [session uid=1337263 pid=774756] Activating service name='org.gnome.ScreenSaver' requested by ':1.27' (uid=1337263 pid=774998 comm="/usr/libexec/gsd-usb-protection " label="unconfined")
Feb  2 09:25:52 9000000741 dbus-daemon[774758]: [session uid=1337263 pid=774756] Successfully activated service 'org.gnome.ScreenSaver'
Feb  2 09:25:52 9000000741 gnome-session-binary[774754]: Entering running state
Feb  2 09:25:52 9000000741 dbus-daemon[774758]: [session uid=1337263 pid=774756] Successfully activated service 'org.gnome.evolution.dataserver.AddressBook10'
Feb  2 09:25:52 9000000741 gnome-shell[774786]: polkitAuthenticationAgent: Received 2 identities that can be used for authentication. Only considering one.
Feb  2 09:25:53 9000000741 gnome-shell[774786]: polkitAuthenticationAgent: Failed to show modal dialog. Dismissing authentication request for action-id org.freedesktop.color-manager.create-profile cookie 28-fd0b6b174ff7f09358072a870c5fdacc-1-c0bee1e759e925b940677a266a4f37a7
Feb  2 09:25:53 9000000741 gnome-shell[774786]: polkitAuthenticationAgent: Received 2 identities that can be used for authentication. Only considering one.
Feb  2 09:25:53 9000000741 gnome-shell[774786]: GNOME Shell started at Thu Feb 02 2023 09:25:52 GMT-0600 (CST)
Feb  2 09:25:53 9000000741 gnome-shell[774786]: Registering session with GDM
Feb  2 09:25:53 9000000741 gnome-session[774754]: gnome-session-binary[774754]: WARNING: Could not get session path for session. Check that logind is properly installed and pam_systemd is getting used at login.
Feb  2 09:25:53 9000000741 gnome-session-binary[774754]: WARNING: Could not get session path for session. Check that logind is properly installed and pam_systemd is getting used at login.
Feb  2 09:25:59 9000000741 gnome-session[774754]: gnome-session-binary[774754]: WARNING: Could not get session path for session. Check that logind is properly installed and pam_systemd is getting used at login.
Feb  2 09:25:59 9000000741 gnome-session-binary[774754]: WARNING: Could not get session path for session. Check that logind is properly installed and pam_systemd is getting used at login.
Feb  2 09:26:01 9000000741 gnome-shell[774786]: JS ERROR: Failed to initialize fprintd service: Gio.IOErrorEnum:


We are testing a product called Exceed TurboX. The product is used to access remote servers in a secure way and several users can access the servers concurrently

We definitely need gdm. I have also discovered that after stopping gdm, I am not able to log out or lock screen.
I then started gdm and I was able to. On checking gmd3 service below are logs.



root@SRA9000000741:~# systemctl status gdm3
&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/lib/systemd/system/gdm.service; static)
     Active: active (running) since Wed 2023-02-01 09:52:51 CST; 1 day 2h ago
    Process: 3418608 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
   Main PID: 3418620 (gdm3)
      Tasks: 3 (limit: 28737)
     Memory: 3.4M
        CPU: 249ms
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;3418620 /usr/sbin/gdm3

Feb 01 10:29:32 SRA9000000741 gdm-password][3512459]: gkr-pam: unable to locate daemon control file
Feb 01 10:29:32 SRA9000000741 gdm-password][3512459]: gkr-pam: stashed password to try later in open session
Feb 02 09:20:20 SRA9000000741 gdm-password][753248]: pam_unix(gdm-password:auth): authentication failure; logname= u>
Feb 02 09:20:21 SRA9000000741 gdm-password][753248]: pam_sss(gdm-password:auth): authentication success; logname= ui>
Feb 02 09:20:21 SRA9000000741 gdm-password][753248]: gkr-pam: unable to locate daemon control file
Feb 02 09:20:21 SRA9000000741 gdm-password][753248]: gkr-pam: stashed password to try later in open session
Feb 02 09:26:06 SRA9000000741 gdm-password][775889]: pam_unix(gdm-password:auth): authentication failure; logname= u>
Feb 02 09:26:07 SRA9000000741 gdm-password][775889]: pam_sss(gdm-password:auth): authentication success; logname= ui>
Feb 02 09:26:07 SRA9000000741 gdm-password][775889]: gkr-pam: unable to locate daemon control file
Feb 02 09:26:07 SRA9000000741 gdm-password][775889]: gkr-pam: stashed password to try later in open session

---

### Post by vanaura on 2023-02-09
Reinstall the login manager

---

