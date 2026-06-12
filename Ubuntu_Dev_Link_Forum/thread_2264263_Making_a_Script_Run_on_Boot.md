---
title: "Making a Script Run on Boot"
date: 2015-02-06
forum: Ubuntu Dev Link Forum
---

### Post by ldavincif on 2015-02-06
Well, I'm making a script for my personal use and for learning purpose. well, once I broke my ubuntu many times experimenting things ^^" I've tried to create a script to install some useful programs and tools for me, and fix a not serious but annoying problem: every time when I turn up my ubuntu my keyboard is in the wrong format, then I always do the command: ```
setxkbmap -model abnt2 -layout br -variant abnt2
``` to fix it.
My script create, after install all my useful stuff,  the following script:
```

#!/bin/sh### BEGIN INIT INFO
# Provides:          abnt2KeyboardSet
# Required-Start:    $local_fs $remote_fs $syslog
# Required-Stop:
# Default-Start:
# Default-Stop:
# Short-Description: seta a formatacao do teclado para abnt2
# Description:       seta a formatacao do teclado para abnt2
### END INIT INFO
#
#/etc/init.d/abnt2KeyboardFixer
#
#
#created by Leonardo Da Vinci to solve the keyboard issue. when the linux inilialize the keyboard will be set to abnt2


case $1 in
    start | restart | reload | force-reload )
        echo "teclado corrigido para o padrao abnt2"
        echo "OBS.: o seu teclado numérico pode ter sido desligado, ligue-o e desligue-o para que volte a funcionar normalmente"
        setxkbmap -model abnt2 -layout br -variant abnt2
        ;;
    stop | status )
        #nothing to be done
        ;;
esac

```
and then it will do the commands
```
sudo mv "$SCRIPTNAME" "$SCRIPTLOCATION"
sudo update-rc.d "$SCRIPTNAME" defaults

```
I've discovered that searching on internet and trying to understand the "Debian policy manual".
But it just is not working, when I turn up my ubuntu I still have the wrong keyboard format =(
Does anyone knows what I'm doing worng?
I'll post my pretty nice script where :D, it may help.
```

#variable of installation
gpp=false
sublime=false
java=false
wine=false


#User interactive variable
installGpp=true
installSublime=true
installJava=true
installWine=true
installScript=true
update=true


#Constants
SCRIPTNAME="abnt2KeyboardFixer"
SCRIPTLOCATION="/etc/init.d/"$SCRIPTNAME""
CIFRAO="$"


#auxiliar variables
nogpp=false
nosublime=false
nojava=false
nowine=false
nofixkeyboard=false


#configurating user entry
for arg in "$@"
do
    case $arg in
        -noupdate )
            update=false
            ;;
        -nogpp )
            installGpp=false
            nogpp=true
            ;;
        -nosublime )
            installSublime=false
            nosublime=true
            ;;
        -nojava )
            installJava=false
            nojava=true
            ;;
        -nowine )
            installWine=false
            nowine=true
            ;;
        -nofixkeyboard )
            installScript=false
            nofixkeyboard=true
            ;;
        -onlygpp )
            if test "$nogpp" = true; then
                echo "as flag -nogpp e -onlygpp obviamente não podem ser usadas ao mesmo tempo! -.-"
                return 1
            fi
            installSublime=false; installJava=false; installWine=false; installScript=false;
            ;;
        -onlysublime )
            if test "$nosublime" = true; then
                echo "as flag -nosublime e -onlysublime obviamente não podem ser usadas ao mesmo tempo! -.-"
                return 1
            fi
            update=false; installGpp=false; installJava=false; installWine=false; installScript=false;
            ;;
        -onlyjava )
            if test "$nojava" = true; then
                echo "as flag -nojava e -onlyjava obviamente não podem ser usadas ao mesmo tempo! -.-"
                return 1
            fi
            installGpp=false; installSublime=false; installWine=false; installScript=false;
            ;;
        -onlywine )
            if test "$nowine" = true; then
                echo "as flag -nowine e -onlywine obviamente não podem ser usadas ao mesmo tempo! -.-"
                return 1
            fi
            installGpp=false; installSublime=false; installJava=false; installScript=false;
            ;;
        -onlyfixkeyboard )
            if test "$nofixkeyboard" = true; then
                echo "as flag -nofixkeyboard e -onlyfixkeyboard obviamente não podem ser usadas ao mesmo tempo! -.-"
                return 1
            fi
            update=false; installGpp=false; installSublime=false; installJava=false; installWine=false;
            ;;
        -removefixkeyboard )
            sudo update-rc.d -f "$SCRIPTNAME" remove
            sudo rm /etc/init.d/"$SCRIPTNAME"
            echo "O grande, delicioso e sexy script \""$SCRIPTNAME"\" script foi removido do seu sistema ='("
            return 0
            ;;
        -h | --help )
            echo "o desenvolvedor ainda não escreveu essa parte do código, desculpe =/"
            echo "mande um e-mail xingando ele!"
            echo "aqui o e-mail do infeliz: lvfs@cin.ufpe.br"
            return 0
            ;;
        * )
            echo "Parametro nao reconhecido.
Se precisar de ajuda execute com o parametro -h ou --help:
sh "$0" -h
ou
sh "$0" --help"
            return 1
    esac
done


#updating
if test "$update" = true; then
    sudo apt-get update
    sudo apt-get upgrade
    clear
else
    echo "udpate NÃO VAI ACONTECER por escolha do usuário"
fi


#checking if g++ is already installed
if test "$installGpp" = true; then
    if ! hash g++; then
        sudo apt-get install build-essential
        gpp=true
    else
        echo "gpp ja esta instalado"
    fi
else
    echo "build-essential NÃO SERÁ INSTALADO por escolha do usuário"
fi


#checking if sublime is already installed
if test "$installSublime" = true; then
    if ! hash ppa:webupd8team/sublime-text-3; then
        echo "Instalando sublime"
        sudo add-apt-repository ppa:webupd8team/sublime-text-3
        sublime=true
    else
        echo "Ja tem sublime"
    fi
else
    echo "sublime NÃO SERÁ INSTALADO por escolha do usuário"
fi


#checking if java is already installed
if test "$installJava" = true; then
    if ! hash ppa:webupd8team/java; then
        sudo add-apt-repository ppa:webupd8team/java
        echo "instalando java"
        java=true
    else
        echo "ja tem java"
    fi
else
    echo "java NÃO SERÁ INSTALADO por escolha do usuário"
fi


#checking if wine is already installed
if test "$installWine" = true; then
    if ! hash ppa:ubuntu-wine/ppa; then
        echo "instalando wine"
        sudo add-apt-repository ppa:ubuntu-wine/ppa
        wine=true
    else
        echo "ja tem wine"
    fi
else
    echo "wine NÃO SERÁ INSTALADO por escolha do usuário"
fi


    #if something wasn't installed, now it's time to update and install it
if test "$gpp" = true || test "$sublime" = true || test "$java" = true || test "$wine" = true; then
    #doesn't matter the user choice in this case, we have to update
    sudo apt-get update


    if test "$sublime" = true; then
        sudo apt-get install sublime-text-installer
    fi


    if test "$java" = true; then
        sudo apt-get install oracle-java8-installer
        sudo apt-get install openjdk-7-jre
        sudo apt-get install openjdk-7-jdk
    fi


    if test "$wine" = true; then
        sudo apt-get install wine1.7
    fi


    #final updates
    if test "$update" = true; then
        sudo apt-get update
        sudo apt-get upgrade
    else
        echo "NOT UPDATED by the user choice"
    fi
    clear
fi


if test "$installScript" = true; then
    if test ! -e "$SCRIPTLOCATION"; then
        #creating the abnt2 keyboard issue script fixer
        echo "#!/bin/sh
### BEGIN INIT INFO
# Provides:          abnt2KeyboardSet
# Required-Start:    "$CIFRAO"local_fs "$CIFRAO"remote_fs "$CIFRAO"syslog
# Required-Stop:
# Default-Start:
# Default-Stop:
# Short-Description: seta a formatacao do teclado para abnt2
# Description:       seta a formatacao do teclado para abnt2
### END INIT INFO
#
#/etc/init.d/$SCRIPTNAME
#
#
#created by Leonardo Da Vinci to solve the keyboard issue. when the linux inilialize the keyboard will be set to abnt2


case ""$CIFRAO"1" in
    start | restart | reload | force-reload )
        echo \"teclado corrigido para o padrao abnt2\"
        echo \"OBS.: o seu teclado numérico pode ter sido desligado, ligue-o e desligue-o para que volte a funcionar normalmente\"
        setxkbmap -model abnt2 -layout br -variant abnt2
        ;;
    stop | status )
        #nothing to be done
        ;;
esac" >> "$SCRIPTNAME"


        #making it executable
        sudo chmod +x "$SCRIPTNAME"
        echo "agora você pode dar o seguinte comando sempre que seu teclado estiver esquisito para ele voltar para a formatação abnt2:
    /etc/init.d/"$SCRIPTNAME" start
embora de todo modo de agora em diante isto não deva mais acontecer ;)
"


        #copying to the right system direcoty
        sudo mv "$SCRIPTNAME" "$SCRIPTLOCATION"


        #make it initialize with the system
        sudo update-rc.d "$SCRIPTNAME" defaults
        echo "pronto, para remover esse script \""$SCRIPTNAME"\", rode este novamente este script com a flag de remoção, assim:
sh "$0" -removefixkeyboard"
    else
        echo "O grande, delicioso e sexy script \""$SCRIPTNAME"\" para fazer o teclado voltar para a formatação abnt2 já está instalado =)"
    fi


    sudo sh "$SCRIPTLOCATION"
else
    echo "script NÃO SERÁ CRIADO E INSTALADO por escolha do usuário"
fi

```

---

### Post by TheFu on 2015-02-06
There are system settings and there are user settings.
At boot, it is generally not possible to set user settings, especially for GUI stuff - like X/Windows.

I think that is the flaw here. It is just a guess.

If you use a GUI login, you can cause user GUI settings to be automatic at login by running your script out of the window manager startup method.  This is dependent on which window manager your version of Ubuntu uses.  I don't run a stock Ubuntu - mine setup uses openbox. [http://openbox.org/wiki/Help:Autostart](http://openbox.org/wiki/Help:Autostart) explains for openbox. Every WM should have a similar how-to.

Of course, you can also fix the root issue by correcting the system console. [http://askubuntu.com/questions/155424/changing-tty-keyboard-layout-on-a-server](http://askubuntu.com/questions/155424/changing-tty-keyboard-layout-on-a-server) At least, that's what I think is the root issue.

---

### Post by Kenneth_Benson on 2015-03-30
Your keyboard setting could actually be put in .bashrc to get it to run on login. The big script would not as you are using sudo's and have to input your password for those.

---

