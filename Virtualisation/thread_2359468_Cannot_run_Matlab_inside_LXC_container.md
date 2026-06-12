---
title: "Cannot run Matlab inside LXC container"
date: 2017-04-24
forum: Virtualisation
---

### Post by denismedeiros on 2017-04-24
Hi guys,

I am trying to run Matlab inside of a LXC container. The host machine is running Ubuntu 16.04 and the container is running the Ubuntu 16.04 as well. The LXC container has the XFCE installed and I can run a lot of gui apps using SSH or VNC. However, the only program I am not able to get working is the Matlab (2016a). I already installed the package as well as the package 'matlab-support'. The installation occurred well, I also could insert the license information, but after finishing everything, I could not run it.


If I run it directly, nothing happens:


```
ubuntu@container:~$ matlab
MATLAB is selecting SOFTWARE OPENGL rendering.
[cursor stops here and nothing happens]

```
I also tried to run with a lot of parameters (-debug, -nodesktop, -nosplash), but the result is the same.
Finally, I tried with '-nosoftwareopengl' and the output was really nothing. :(

```
ubuntu@container:~$ matlab -nosoftwareopengl
[cursor stops here and nothing happens]

```

Can anyone help me with this? I don't think it is a problem with the X, since other apps run normally.

Bellow, some information about environment variables:

```

LESSOPEN=| /usr/bin/lesspipe %s
ARCH=glnxa64
PULSE_CLIENTCONFIG=/home/ubuntu/.x2go/C-ubuntu-50-1492725703_stDXFCE_dp24/.pulse-client.conf
MAIL=/var/mail/ubuntu
SSH_CLIENT=10.9.99.167 37326 22
USER=ubuntu
SSH_AGENT_PID=58666
LD_LIBRARY_PATH=/usr/local/MATLAB/R2016a/sys/opengl/lib/glnxa64:/usr/local/MATLAB/R2016a/sys/os/glnxa64:/usr/local/MATLAB/R2016a/bin/glnxa64:/usr/local/MATLAB/R2016a/extern/lib/glnxa64:/usr/local/MATLAB/R2016a/sys/java/jre/glnxa64/jre/lib/amd64/native_threads:/usr/local/MATLAB/R2016a/sys/java/jre/glnxa64/jre/lib/amd64/server:/usr/lib/nx/X11/Xinerama:/usr/lib/nx/X11
SHLVL=4
HOME=/home/ubuntu
OLDPWD=/usr/local/MATLAB/R2016a
AUTOMOUNT_MAP=
BASEMATLABPATH=
QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-2dP0ycLq8k,guid=a4f72bde5597c5641336151a58f92fca
COLORTERM=xfce4-terminal
XSESSION_EXEC=xfce4-session
LOGNAME=ubuntu
WINDOWID=35660512
_=/usr/local/bin/matlab
MATLABPATH=/usr/local/MATLAB/R2016a/toolbox/local
X2GO_AGENT_PID=58360
XDG_SESSION_ID=c2
TERM=xterm
STARTUP=/usr/bin/dbus-launch --exit-with-session /usr/bin/env LD_LIBRARY_PATH=/usr/lib/nx/X11/Xinerama:/usr/lib/nx/X11 xfce4-session
PATH=/home/ubuntu/bin:/home/ubuntu/.local/bin:/usr/local/bin:/usr/bin:/bin
SESSION_MANAGER=local/container:@/tmp/.ICE-unix/58583,unix/container:/tmp/.ICE-unix/58583
QT_GRAPHICSSYSTEM=native
XDG_RUNTIME_DIR=/run/user/1000
DISPLAY=:50.0
TOOLBOX=/usr/local/MATLAB/R2016a/toolbox
LANG=pt_BR.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
XAUTHORITY=/home/ubuntu/.Xauthority
SSH_AUTH_SOCK=/tmp/ssh-mTxWmYkCQnRu/agent.58665
SHELL=/bin/bash
MATLAB=/usr/local/MATLAB/R2016a
XFILESEARCHPATH=/usr/local/MATLAB/R2016a/sys/java/jre/glnxa64/jre/lib/locale/%L/%T/%N%S:
QT_ACCESSIBILITY=1
LESSCLOSE=/usr/bin/lesspipe %s %s
OSG_LD_LIBRARY_PATH=/usr/local/MATLAB/R2016a/sys/openscenegraph/lib/glnxa64
PWD=/home/ubuntu
SSH_CONNECTION=10.9.99.167 37326 10.0.3.102 22
X2GO_SESSION=ubuntu-50-1492725703_stDXFCE_dp24
NX_XINERAMA_CONF=/home/ubuntu/.x2go/C-ubuntu-50-1492725703_stDXFCE_dp24/xinerama.conf



```

[FONT=Verdana]Thanks![/FONT]

---

