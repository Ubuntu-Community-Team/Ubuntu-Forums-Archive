---
title: "mixxx dj goodies"
date: 2011-05-29
forum: Ubuntu Studio
---

### Post by boblizar on 2011-05-29
open synaptic, click settings, repositories

then add ppa:mixxx/mixxx

then update, then search for mixxx and easytag-aac

i changed my lauching file for mixxx to make it play more nicely with my systems audio

ill be a punk and jack linux from scratches methods of kicking ***

```

sudo su

```
```

rm /usr/share/applications/mixxx.desktop
cat > /usr/share/applications/mixxx.desktop << "EOF"
[Desktop Entry]
Version=1.0
Name=Mixxx
GenericName=Digital DJ interface
Comment=A digital DJ interface
Exec=mixxx
Terminal=false
Icon=mixxx-icon
Type=Application
StartupNotify=true
Categories=Qt;AudioVideo;Audio;
EOF
chmod 644 /usr/share/applications/mixxx.desktop
exit

```

---

