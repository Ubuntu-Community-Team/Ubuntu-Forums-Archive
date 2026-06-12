---
title: "Idea for ubuntu developers: The Kurumin Example"
date: 2005-06-18
forum: The Cafe
---

### Post by sapo on 2005-06-18
As you may already know, i m brazillian and here we have a pretty famous distro among newbies, this distro is called "kurumin".

Today i was reading the newsforge website and i found this article:

[http://os.newsforge.com/os/05/06/10/184203.shtml?tid=152&tid=2](http://os.newsforge.com/os/05/06/10/184203.shtml?tid=152&tid=2)

The big difference between kurumin and the other distros are those "magic icons" that in fact are only scripts, but for noobs its the best part, cause they dont want to think about what to do, they just want to click and make it work (the name of the panel is "Clica aqui" that means, "click here").

Among the "clica aqui" scripts, there are scripts to detect and install winmodens, install wireless, configure a firewall, etc...

So, it has more than 400 scripts as mentioned in the newsforge article.

And i think that ubuntu filosophy is near the kurumin linux, the "clica aqui"  and the "just works" seems very similar to me.

What do you think about it? i think that i could become a 3rd party project to make several scripts for noobs, i ve never used kurumin so i cant say more about it.. but they have scripts that makes almost everything automatically without thinking about complicated stuff...

And if you want to download the livecd to see how it works:
[http://www.guiadohardware.net/kurumin/#download](http://www.guiadohardware.net/kurumin/#download)

And here a screenshot of the "clica aqui" panel:
[http://www.guiadohardware.net/kurumin/screenshots/4.0/snapshot6.png](http://www.guiadohardware.net/kurumin/screenshots/4.0/snapshot6.png)

I think that most of you will not understand the portuguese words, but if you take a look each button will install something.. from a playstation joystick in a paralell port (very common here in brazil), printer, install and download pictures from a digicam, and a lot of scripts to share the internet connection, install apache, samba, vnc.

And take a look at the first button of the window in focus, it installs: apache + php + mysql + phpbb + noip, with a single click  :grin: 

And all these scripts uses apt-get to install it all ;)

---

### Post by ubuntu_demon on 2005-06-18
[QUOTE=sapo]As you may already know, i m brazillian and here we have a pretty famous distro among newbies, this distro is called "kurumin".

Today i was reading the newsforge website and i found this article:

[http://os.newsforge.com/os/05/06/10/184203.shtml?tid=152&tid=2](http://os.newsforge.com/os/05/06/10/184203.shtml?tid=152&tid=2)

The big difference between kurumin and the other distros are those "magic icons" that in fact are only scripts, but for noobs its the best part, cause they dont want to think about what to do, they just want to click and make it work (the name of the panel is "Clica aqui" that means, "click here").

Among the "clica aqui" scripts, there are scripts to detect and install winmodens, install wireless, configure a firewall, etc...

So, it has more than 400 scripts as mentioned in the newsforge article.

And i think that ubuntu filosophy is near the kurumin linux, the "clica aqui"  and the "just works" seems very similar to me.

What do you think about it? i think that i could become a 3rd party project to make several scripts for noobs, i ve never used kurumin so i cant say more about it.. but they have scripts that makes almost everything automatically without thinking about complicated stuff...

And if you want to download the livecd to see how it works:
[http://www.guiadohardware.net/kurumin/#download](http://www.guiadohardware.net/kurumin/#download)[/QUOTE]
 seems a nice idea!

can we use kurumin in english to check it out ?

---

### Post by sapo on 2005-06-18
[QUOTE=demon666_nl]seems a nice idea!

can we use kurumin in english to check it out ?[/QUOTE]


I think so, the kde and all other apps i m sure you can install in english, but i think that the "clica aqui" stuff is just in portuguese

---

### Post by weekend warrior on 2005-06-18
The Kanotix community also uses scripts quite a bit. There are a bunch of them in /usr/local/bin  A few of them are up on [Kano's Scriptpage](http://kanotix.com/files/). 

It's a good idea in my view. They can be pretty useful to have around if you come across a particular need that's covered by one of them.

---

### Post by tristan on 2005-06-19
There are a couple of excellent scripts I've seen floating around ubuntuforums which automate some of the most common tasks new ubuntu users perform (eg setting up repositories, installing useful codecs and winfonts etc). 

It'd be a great idea to have a handful of scripts for the most common tasks present by default on a fresh ubuntu desktop. eg

setup dialup internet access
install mp3 and other proprietary codecs
install java  

This would get around ubuntu not actually technically being allowed to include non free software by default (in the case of codecs especially) and would eliminate 98% of the newbie complaints I've seen :)

---

### Post by mtron on 2005-06-19
[QUOTE=tristan]There are a couple of excellent scripts I've seen floating around ubuntuforums [/QUOTE]

Sounds really a good idea. we could make a zenity dialog for gnome like in the png for kde. and make it so eg. the "after install helper" and other scripts more newbie friendly.

Sounds like a good idea for a new "ubuntuforums project"

would sb. be interrested to help collecting, testing and writing some scripts?

---

### Post by sapo on 2005-06-19
[QUOTE=mtron]Sounds really a good idea. we could make a zenity dialog for gnome like in the png for kde. and make it so eg. the "after install helper" and other scripts more newbie friendly.

Sounds like a good idea for a new "ubuntuforums project"

would sb. be interrested to help collecting, testing and writing some scripts?[/QUOTE]

Thats the ideia.. i personally have used that "automated script for new users" and it was very helpfull.. and i used some scripts from ubuntu forums too  :grin:

---

### Post by Lovechild on 2005-06-19
break the law vs. encouraging the use of open standards and formats - you pick

---

### Post by sapo on 2005-06-19
[QUOTE=Lovechild]break the law vs. encouraging the use of open standards and formats - you pick[/QUOTE]


hum.. the idea is not to break any laws.. if the ubuntu developers doesnt feel like using proprietary software or this kind of stuff, we still can make a lot of scripts with free software, scripts to detect and configure some hardwares, install some add-ons, customize the installation, install kde in Ubuntu and Gnome in Kubuntu... a lot of things can be mado to "make it easy"


And we can have a "3rd party application" with non-free software, that any user can download the scripts and install if they want

---

### Post by mtron on 2005-06-19
What's the problem when you give existing scripts a nice polish and download some software from the repos? 

And also when the devels don't want to include it in the standard install, we can make a downloadable version, that creates a menu enty for the script.

So i don't think that there will be similar problems like the add-on cd had. cause when you don't ship these packages, where's the problem with the (US) law?

---

### Post by rubycon on 2005-06-19
I'm working on a similar project myself for the ubuntu community. It's a tool to create graphical wizards running scripts. The wizards are made up of simple xml files. I began the work just a couple of weeks ago and plan on having it ready later this summer. Still people would have to write the scripts but this application could be used as a little more user friendly way of presenting them.

---

### Post by sapo on 2005-06-19
[QUOTE=mtron]What's the problem when you give existing scripts a nice polish and download some software from the repos? 

And also when the devels don't want to include it in the standard install, we can make a downloadable version, that creates a menu enty for the script.

So i don't think that there will be similar problems like the add-on cd had. cause when you don't ship these packages, where's the problem with the (US) law?[/QUOTE]


thats the point...

So, i m feeling like starting some kind of "project scrap" i m not good at programing (i program php for food and thats all) but we can start a brainstorming and maybe start a 3rd party project.

what do you guys think about it?

I have a image in my brain of how it is going to work...

The user download the .deb package or something like it, with all the scrips, then it creates a icon on his desktop.

When he open this icon the magic stuff happens  :grin: 

A lot of buttons that each click will perform something.. to detecting his hardware, oppening a wizard to configure it, or install codecs, apps, java, flash, etc etc.

Its like that "Script for new users" but they could install one by one.

We could talk to the guy who has made this script to make it behave this way... there's a lot of possibilities...  :grin:

---

### Post by sapo on 2005-06-19
yo fellows... i was browsing the kurumin forums and found this example script to make a "magic icon"

```

#!/bin/sh 
# Script modelo para os ícones mágicos 
# Escrito por Carlos E. Morimoto 

# Esta função descobre se o script está sendo executado no modo gráfico ou em modo texto. 
# Caso esteja no modo gráfico é usado o Xdialog, caso contrário ele usa o antigo dialog. 
# O dialog não suporta todas as funções do Xdialog, por isso nem sempre é possível que o mesmo script 
# rode tanto no modo texto quanto no modo gráfico sem alterações. Em muitos casos você vai precisar de 
# uma boa dose de criatividade. 
# A documentação do Xdialog está disponível em: http://thgodef.nerim.net/xdialog/doc/index.html 
# 

case "`tty`" in 
/dev/tty[1-8]) 
MODE=text 
DIALOG=dialog 
;; 
/dev/pts/*|/dev/ttyp*) 
MODE=x 
export XDIALOG_HIGH_DIALOG_COMPAT=1 
[ -x /usr/bin/gdialog ] && DIALOG=gdialog 
[ -x /usr/bin/Xdialog ] && DIALOG=Xdialog 
[ $DIALOG = dialog ] && MODE=text 
;; 
*) 
esac 

# Esta é a função que cria o menu com as opções. 
# Nesta parte vai uma linha para cada opção. Mais abaixo cada uma destas linhas ganha uma seção separada, 
# onde vão os comandos executados por cada uma. 

$DIALOG --title "Ícones mágicos" \ 
--backtitle " Instalar " \ 
--radiolist "Descrição 
" 24 70 0 \ 
"Instalar" "Instalar e abrir o programa" off \ 
"Remover" "Remover o programa depois de instalado" off \ 
"Abrir" "Abrir o programa depois de instalado" off \ 
"Sair" "Sair sem fazer nada" off 2> /tmp/checklist.tmp.$$ 
retval=$? 


# Esta função fecha o script caso seja pressionado o botão "cancelar". 
if [ $retval = 1 ]; 
then 
exit 0 
fi 

# Caso seja escolhida qualquer uma das opções e pressionado o botão "ok", o script procura pela seção 
# referente à seção escolhida e executa os comandos dentro dela. 
# Cada seção começa no "if" e termina no "fi" 

choice=`cat /tmp/checklist.tmp.$$` 
rm -f /tmp/checklist.tmp.$$ 


# ----------------------------------- 

if [ "$choice" = "Instalar" ]; 
then 

# Aqui vão os comandos que instalam o programa. As instalação mais simples simplesmente usam o apt-get, 
# como em "apt-get install frozen-bubble". mas você pode usar comandos diversos em shell para instalar programas 
# mais complicados. Consulte os scripts instalar-oo, instalar-java, etc. para alguns exemplos. 
# O "apt-get -f install" serve para "limpar a casa" antes de começar a instalação, para o caso do apt estar travado 
# por causa de uma instalação anteror mal-sucedida. 

sudo apt-get -f install 

sudo apt-get install 

# O sleep faz o script para por alguns segundos, de forma que o usuário possa ver alguma mensagem de erro 
# que surja durante a instalação. 

sleep 8 

# Esta função cria o ícone no menu iniciar do KDE. Muitos pacotes criam a entrada no menu automaticamente, 
# por isso esta seção nem sempre é necessária. 

echo "Criando ícone no Menu..." 

# Preencha os campos abaixo com as informações sobre o programa instalado, como em: 
# nomeapp="Mozilla" (o nome do programa, que será usado como nome de arquivo e como entrada no menu) 
# execapp="mozilla" (o comando de terminal que abre o programa, em geral é o próprio nome, escrito em minúsculas) 
# catapp="Internet" (a pasta dentro do iniciar onde o ícone será colocado. O iniciar do KDE vai dentro da pasta /usr/share/applnk) 
# - Algumas categorias são: Editors (editores), Games, Graphics, Internet, Multimedia, Office (escritório), System, Utilities (utilitários) e Development 
# iconeapp="mozilla" (o ícone que aparecerá no menu. Veja os disponíveis na pasta /usr/share/icons/crystalsvg/ 

nomeapp="" 
execapp="" 
catapp="" 
iconeapp="" 

# Esta é a função que "escreve" o ícone usando as informações colocadas acima. Como você pode ver, os ícones 
# do menu do KDE nada mais são do que arquivos de texto que seguem uma certa sintaxe: 

cat <<EOF >/tmp/$nomeapp.desktop 
[Desktop Entry] 
Encoding=UTF-8 
Name=$nomeapp 
Exec=$execapp 
X-KDE-Library=libkwordpart 
GenericName= 
MimeType= 
Type=Application 
Icon=$iconeapp 

EOF 

sudo cp -a /tmp/$nomeapp.desktop /usr/share/applnk/$catapp/$nomeapp.desktop 
mkdir -p ~/.kde/share/applnk/$catapp/ 
cp -a /tmp/$nomeapp.desktop ~/.kde/share/applnk/$catapp/$nomeapp.desktop 
rm -f /tmp/$nomeapp.desktop 

## 

# Estas são algumas funções que você pode usar para incrementar seu script, exibindo uma janela adicional, com instruções 
# de uso ou adicionando a opção de instalar mais componentes por exemplo. 

# # Isto é um exemplo de caixa de texto 

# BT="Ícones mágicos" 
# T1="Título que vai dentro da janela" 
# M1="Aqui vai o texto da mensagem." 
# $DIALOG --backtitle "$BT" --title "$T1" --msgbox "$M1" 20 75 
# # (os dois números indicam o tamanho da janela, em caracteres) 


# # Isto é um exemplo de if, ou seja, uma pergunta. 

# BT="Ícones mágicos" 
# T1="Título que vai dentro da janela" 
# M1="Aqui vai o texto da pergunta" 
# $DIALOG --title "$T1" --yesno "$M1" 18 60 
# x=$? 

# # Caso seja pressionado o botão "ok", são executados os comandos abaixo. Caso seja pressionado o botão "cancel" 
# # a função não faz nada. 

# if [ $x = 0 ] ; then 

# Aqui vão os comandos que serão executados 
# echo "olá" 

# fi 


# Aqui termina a função de instalação. 

fi 

# ----------------------------------- 

if [ "$choice" = "Remover" ]; 
then 

# Coloque aqui os comandos que srão executados quando for usada a opção "remover" na janela principal. 
# o objetivo é que esta função desinstale completamente o aplicativo, revertendo os passos realizados na 
# função de instalar. 

sudo apt-get remove 

sleep 5 


fi 

# ----------------------------------- 


if [ "$choice" = "Abrir" ]; 
then 

# Aqui vai o comando de terminal que abre o programa. em geral é o próprio nome do programa, escrito em minúsculas 

sleep 1 

fi 

# ----------------------------------- 

if [ "$choice" = "Sair" ]; 
then 

exit 0 

fi 



exit 0

```

If you like i can translate the comments.. but theres no need for it.. its really simple i think.. i will find more examples to show you how it works.. and i m starting to study python to start a gui or something like it [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

**Here a script to install gnome on kurumin.. very simple i think**

```

#!/bin/sh
# Script de instalação dos ícones mágicos
# Escrito por Carlos E. Morimoto
 

sudo-verificar
if [ "$?" = "2" ]; then exit 0; fi

case "`tty`" in
/dev/tty[1-8])
MODE=text
DIALOG=dialog
;;
/dev/pts/*|/dev/ttyp*)
MODE=x
export XDIALOG_HIGH_DIALOG_COMPAT=1
[ -x /usr/bin/gdialog ] && DIALOG=gdialog
[ -x /usr/bin/Xdialog ] && DIALOG=Xdialog
[ $DIALOG = dialog ] && MODE=text
;;
*)
esac


$DIALOG --title "UmClique" \
--backtitle " Instalar o Gnome2 no Kurumin " \
--radiolist "O Gnome dispensa comentários. Este ícone mágico se encarrega de instalar o Gnome e fazer uma configuração básica para adequar 
as configurações default. Serão baixados cerca de 50 MB de pacotes, por isso a instalação é recomendada apenas para quem acessa via banda larga. 
" 21 70 0 \
"Instalar" "Instalar o Gnome 2" off \
"Sair" "Sair sem fazer nada" off 2> /tmp/checklist.tmp.$$
retval=$?

if [ $retval = 1 ];
then
  exit 0
fi

choice=`cat /tmp/checklist.tmp.$$`
rm -f /tmp/checklist.tmp.$$

# -----------------------------------

if [ "$choice" = "Instalar" ];
then

sudo apt-get -f install
sudo dpkg --configure -a

sudo apt-get install gnome-core
sudo apt-get install xscreensaver
sudo apt-get install xscreensaver-gnome
sudo apt-get install gconf-editor

rm -f ~/.xmodmap
sudo rm -f /etc/skel/.xmodmap

sudo apt-get -f install 


kdialog --msgbox "Para usar o Gnome, clique no botão K > Sair Knoppix e na tela de login escolha a opção gnome-desktop. 
A partir daí o Gnome virará o desktop padrão do sistema, para voltar a usar o KDE dê um logout no Gnome e, de volta voltar à tela de login e escolha o KDE." --title "Aviso"



fi

# -----------------------------------

if [ "$choice" = "Remover" ];
then

sudo apt-get remove 

sleep 5


fi

# -----------------------------------


if [ "$choice" = "Abrir" ];
then



fi

# -----------------------------------

if [ "$choice" = "Sair" ];
then

exit 0

fi



exit 0

```

---

### Post by Lovechild on 2005-06-19
[QUOTE=sapo]hum.. the idea is not to break any laws.. if the ubuntu developers doesnt feel like using proprietary software or this kind of stuff, we still can make a lot of scripts with free software, scripts to detect and configure some hardwares, install some add-ons, customize the installation, install kde in Ubuntu and Gnome in Kubuntu... a lot of things can be mado to "make it easy"


And we can have a "3rd party application" with non-free software, that any user can download the scripts and install if they want[/QUOTE]

You call it "doesn't feel like", I call it "welcome to license violation and patent law"

detect/configure hardware, look up HAL it's exactly what you want

install addons, what addons, and would it help to have a little app to apt-get e.g. mp3 gstreamer plugins and such - there are valid reasons why Ubuntu can't ship such things, I'm unsure if the fact that they ship a script to install mp3 support would be considered vendor distribution - the sane thing here would be to advocate open formats and standards and explain the issue to the user, not provide a workaround to the issue.

kde/gnome in ubuntu/gnome - apt-get it, I'm sure the app-install program would fix that - but why would the average user want to do that, we need a consistent platform.

---

### Post by mtron on 2005-06-19
[QUOTE=Lovechild] I call it "welcome to license violation and patent law".[/QUOTE]

Well, that's something we should really think about. can we have some more opinions from some mods please, also we should write to Matt, and see if there is a possibility that they take it in the standard distro, and what he thinks about it...

I

---

### Post by sapo on 2005-06-19
[QUOTE=Lovechild]You call it "doesn't feel like", I call it "welcome to license violation and patent law"

detect/configure hardware, look up HAL it's exactly what you want

install addons, what addons, and would it help to have a little app to apt-get e.g. mp3 gstreamer plugins and such - there are valid reasons why Ubuntu can't ship such things, I'm unsure if the fact that they ship a script to install mp3 support would be considered vendor distribution - the sane thing here would be to advocate open formats and standards and explain the issue to the user, not provide a workaround to the issue.

kde/gnome in ubuntu/gnome - apt-get it, I'm sure the app-install program would fix that - but why would the average user want to do that, we need a consistent platform.[/QUOTE]

Btw you are talking as a user.. i m thinking about newbies that dont know what the hell is apt-get and dont know how to do simple things..

and there are a lot of free apps that can be installed.. just a few examples: Azureus, Avidemux2, mozilla-thunderbird, wine, a firewall like firestarter, ati and nvidia drivers, some editors like NVU, bluefish, amule, gnome-baker, gdesklets, and a lot more.

I m thinking about newbies that NEVER used linux and dont know how to install and configure this things.. or some lazy guy like me that knows how to do it by hand but thinks that clicking in a single button is better than typing a lot of apt-get commands in a terminal.

The ideia is not to install proprietary software  ](*,)  but to make it easier to install some usefull stuff that didnt come with the defaul installation...

---

### Post by Lovechild on 2005-06-19
note to you, the ati/nvidia drivers are NOT free software

---

### Post by tread on 2005-06-19
When you say ati/nvidia drivers aren't free, you are talking gpl, right? Cos if they are free (monetarily) then I think a script should exist to install them .. new Linux users don't care about the GPL or even understand what it means. 

I think this is a good idea, I did put up a suggestion on a thread once about using scripts but I had a rough idea in mind. This looks like it will be more polished, and I really like the idea of it being in the application menu. One more suggestion: the application should be able to query some website and get a list of scripts or update itself. 

Rubycon, could we see some screenshot or better yet, some code we could compile and test? It would be nice, and if you have a standard scripting interface we could start making scripts from the ubuntuguide already.

---

### Post by tread on 2005-06-19
One more thing: to Rubycon.

The actions in the application you are building could also be categorized?
I appreciate you wouldn't be able to do everything now :) but if its in the framework someone could add it later.

---

### Post by sapo on 2005-06-19
[QUOTE=Lovechild]note to you, the ati/nvidia drivers are NOT free software[/QUOTE]

i m not talking about FREE SOFTWARE, but free "of charge" software.

If you are going just to use GPL in you life, you are NOT going to have 3d, you are not going to watch dvd, not going to listen to mp3.. so its better to dont use the pc at all...

i m using Opera 8.0 right now.. any problems with this? isnt free... and so what? am i gonna die cause i m using opera instead o firefox?  :roll:

Opera isnt "free software", but you can download and use it, as long as you dont mind with the banner... whats the problem in using it?

---

### Post by tread on 2005-06-19
Let's not fight about free and free software, lets develop this and then ask for it to be included in the standard installation. Even if its not included, we can put it up somewhere and point newbies to it.

---

### Post by sapo on 2005-06-19
[QUOTE=tread]Let's not fight about free and free software, lets develop this and then ask for it to be included in the standard installation. Even if its not included, we can put it up somewhere and point newbies to it.[/QUOTE]

yep thats the point..

it could have some scripts with "free software" in the Ubuntu cd, and from there point the users to a website to download more scripts, etc

---

### Post by Lovechild on 2005-06-19
[QUOTE=sapo]i m not talking about FREE SOFTWARE, but free "of charge" software.

If you are going just to use GPL in you life, you are NOT going to have 3d, you are not going to watch dvd, not going to listen to mp3.. so its better to dont use the pc at all...

i m using Opera 8.0 right now.. any problems with this? isnt free... and so what? am i gonna die cause i m using opera instead o firefox?  :roll:

Opera isnt "free software", but you can download and use it, as long as you dont mind with the banner... whats the problem in using it?[/QUOTE]


Did I attack you, no I did not, I merely pointed out that you placed a piece of software that isn't free in the free pile - also those two kernel modules are known to cause serious problems - I personally have an nvidia card but I use the free nv driver since it works best for my needs. I will buy and support any 3d card with open specs and drivers though.

I don't need mp3 support, I paid for my cds, I rip them in ogg vorbis for save keeping and I actively encourage people to do the same, do you have a problem with me advocating a legally safe and technically better alternative? The MP3 patents especially represent the nutty nature of epatents, they actaully patented math, math which btw. is highly contested.

I don't especially need DVD support either, but I would like it so I can back my DVDs up in Ogg Theora files, sadly I cannot legally do that right now so I'll work on making it so instead of whining. 

So have you written your elected officials and told them about your concerns about epatents and the implications it will have on innovation in the IT field - I have and most of them got back to me with well worded replies

All of what you want can be done with free software (except stuff like the nvidia driver of course provided you want accelerated 3d), I am merely pointing out that it does not solve the problem to pave over it with easy to use patent/license violation frontends, we do need to inform the public about why things are as they are. I, for one, would like nothing more than to have NTFS resizing in the Fedora Core installer (sorry I use FC not ubuntu - both are excellent though), since it's one of the most useful features when deploying Linux on people's Windows XP machines. I would like to be able to play mp3 files or any number of video formats, but I understand why I can't and is it should a big crime to want to fight back?

But that being said, go ahead and make your frontend to apt-getting the needed files, I imagine it could be a fun little project and hopefully it will make life easier for some people.

---

### Post by sapo on 2005-06-19
[QUOTE=Lovechild]But that being said, go ahead and make your frontend to apt-getting the needed files, I imagine it could be a fun little project and hopefully it will make life easier for some people.[/QUOTE]

Ok.. everyone have different ways of thinking about the same stuff.

Personally i think that most of my friends.. yes i gave them ubuntu.. some i spent 3 days of my useless life teaching them how to install it, how to install this and that softwares.. and after all that time that i spent they say to me:

"I didnt manage how to install my ATI card, so i unistalled Ubuntu"

"I cant acess my bank account cause the java isnt working in my browser, an i cant install flash in my amd64"

"I ve installed it, cause is so fucking hard to install a program, i dont understand english so i dont know wtf is written in the README, and i dont know either wtf the error says when i type ./configure"

All these things make me really sad.. you dont know why?

Cause i gave them the ubuntu cd not to make them play with it and then trash it.. but i gave them the cd hoping that they could love it like i do and use it as they primary OS.. but because of some small things.. they ALL end up giving up and formating the partition as NTFS again.. and that makes me really said.

So.. the ideia is to HELP these kind of user, no more than it.. if those patent stuff hurt your pride.. thats YOUR problem.. 

I think that none of my these are gonna say "I will convert all my mp3 to OGG cause mp3 isnt free".

They would rater say: "I will unistall this OS cause it cant play my mp3"

Thats the truth.. you like it or not... and "if you cant beat the enemys, join them"

I dont like this patent, non-free, and all this stuff too.. but life is really hard without it...

---

### Post by verbalshadow on 2005-06-19
[QUOTE=sapo]Ok.. everyone have different ways of thinking about the same stuff.

Personally i think that most of my friends.. yes i gave them ubuntu.. some i spent 3 days of my useless life teaching them how to install it, how to install this and that softwares.. and after all that time that i spent they say to me:

"I didnt manage how to install my ATI card, so i unistalled Ubuntu"

"I cant acess my bank account cause the java isnt working in my browser, an i cant install flash in my amd64"

"I ve installed it, cause is so fucking hard to install a program, i dont understand english so i dont know wtf is written in the README, and i dont know either wtf the error says when i type ./configure"

All these things make me really sad.. you dont know why?

Cause i gave them the ubuntu cd not to make them play with it and then trash it.. but i gave them the cd hoping that they could love it like i do and use it as they primary OS.. but because of some small things.. they ALL end up giving up and formating the partition as NTFS again.. and that makes me really said.

So.. the ideia is to HELP these kind of user, no more than it.. if those patent stuff hurt your pride.. thats YOUR problem.. 

I think that none of my these are gonna say "I will convert all my mp3 to OGG cause mp3 isnt free".

They would rater say: "I will unistall this OS cause it cant play my mp3"

Thats the truth.. you like it or not... and "if you cant beat the enemys, join them"

I dont like this patent, non-free, and all this stuff too.. but life is really hard without it...[/QUOTE]
 i think the frontend should divide the software into Freeware and free software to helping new users to understand the difference and making things easier for Free Software only users also.

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=sapo]
Personally i think that most of my friends.. yes i gave them ubuntu.. some i spent 3 days of my useless life teaching them how to install it, how to install this and that softwares.. and after all that time that i spent they say to me:[/QUOTE]


You should have done it for them. Most people can't even install Windows and get all the drivers and codecs to work. They pay Dell or some nerd to do it for them.

If my friends would have come to me with those problems I would have SSHed in and fixed it for them. Not that I'm ragging on you or nothing, but if you want to spread Ubuntu you got to go the extra mile. Great thing about Linux....


I see your point about the scripts, but please note that:

1. For most things that are not proprietary problems, the devs want to make those things setup during the install. They are working hard on the adding new hardware support I hear.

2. For proprietary stuff...the devs won't go for this. Many of them are very big on OSS (Mark- the guy who pays for it all- is too), so at most you would see maybe a script for the Ati and Nvidia drivers and maybe a Gui tool for ndiswrapper. Codecs and Java and that stuff...the best Ubuntu will ever have by default is the OSS equivelents preinstalled (OSS java, OSS flash, etc.). Its because of the philosophy of the whole group up top. If you need that stuff, Linspire is waiting for a new customer.

3. On the other hand, this WOULD make a great third party project and if someone wanted to start creating and collected scripts into one place I'm sure that we can find some place on the forum to host such things. All the scripts now are spread of a dozens threads....it would be nice to have them in the same place.

> Thats the truth.. you like it or not... and "if you cant beat the enemys, join them"

Mark (again the guy paying the bills) would rather Ubuntu go away than turn into Linspire.

---

### Post by mtron on 2005-06-19
[QUOTE=sapo]yo fellows... i was browsing the kurumin forums and found this example script to make a "magic icon"[/QUOTE]

Yea, a good point to start! the install script is pretty much self-explaining, but xdialog does not come with the standard install, so we should rewrite it using zenity. (integrates also in gnome)

Radioboxes are no problem, i'll try to make an example. 

But much more interresting: we need to create the basic interface (panel) like on your screenshot [here](http://www.guiadohardware.net/kurumin/screenshots/4.0/snapshot6.png) , who would be interrested in creating this for our gnome desktop?

also a status would be nice that shows which programs are already installed.

So a nice thing to try...

---

### Post by Lovechild on 2005-06-19
[QUOTE=sapo]Ok.. everyone have different ways of thinking about the same stuff.

Personally i think that most of my friends.. yes i gave them ubuntu.. some i spent 3 days of my useless life teaching them how to install it, how to install this and that softwares.. and after all that time that i spent they say to me:

"I didnt manage how to install my ATI card, so i unistalled Ubuntu"

"I cant acess my bank account cause the java isnt working in my browser, an i cant install flash in my amd64"

"I ve installed it, cause is so fucking hard to install a program, i dont understand english so i dont know wtf is written in the README, and i dont know either wtf the error says when i type ./configure"

All these things make me really sad.. you dont know why?

Cause i gave them the ubuntu cd not to make them play with it and then trash it.. but i gave them the cd hoping that they could love it like i do and use it as they primary OS.. but because of some small things.. they ALL end up giving up and formating the partition as NTFS again.. and that makes me really said.

So.. the ideia is to HELP these kind of user, no more than it.. if those patent stuff hurt your pride.. thats YOUR problem.. 

I think that none of my these are gonna say "I will convert all my mp3 to OGG cause mp3 isnt free".

They would rater say: "I will unistall this OS cause it cant play my mp3"

Thats the truth.. you like it or not... and "if you cant beat the enemys, join them"

I dont like this patent, non-free, and all this stuff too.. but life is really hard without it...[/QUOTE]

You seem to be taking this awfully personal.. chill please, for the sake of your health.

The good news for your friends, both flash and java should become much better soon, my FC4 ships with working 100% free java, and gcjwebplugin gets me java in my browser should I so desire (I just happen not to right now for security issues)
And swfdec and gplflash are working on flash7 compatability, sources tell me it's working.. sorta so giving a bit more time you'll have flash.

But we cannot be held accountable for the legal issues, and people need to understand that.

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=Lovechild]
The good news for your friends, both flash and java should become much better soon, my FC4 ships with working 100% free java, and gcjwebplugin gets me java in my browser should I so desire (I just happen not to right now for security issues)
And swfdec and gplflash are working on flash7 compatability, sources tell me it's working.. sorta so giving a bit more time you'll have flash.
[/QUOTE]

I think this is a much better long term option.

---

### Post by TravisNewman on 2005-06-19
This is a great idea-- if you only ship the script and the user runs the script to download the file, then I think legal issues are shifted to the user. But regardless, even staying totally Free this would be helpful.

And I'm looking forward to the GPLed Java and Flash. I hope they're all their cracked up to be.

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=panickedthumb]This is a great idea-- if you only ship the script and the user runs the script to download the file, then I think legal issues are shifted to the user. But regardless, even staying totally Free this would be helpful.[/QUOTE]

I think we agree then- the forum will help in the effort.

[QUOTE=panickedthumb]
And I'm looking forward to the GPLed Java and Flash. I hope they're all their cracked up to be.[/QUOTE]

They will never be any good if the major distos ship with closed software.

---

### Post by mtron on 2005-06-20
So i think the panel should be made in C , with the gtk+ 2.0. 

I never worked with it, but this panel should not need  complex programming. Except, it would be nice to display the script status  in an embedded terminal, like synaptic does it, but for the beginning a basic interface with some buttons and tabs should do it

Is someone else interrested, who has some experience with gtk in programming the panel ?

If not, i'll try it, but it will take me some time to figure out the basics.

A good tutorial for gkt+ 2.0 that covers our needs for this small programm is [here](http://www.gtk.org/tutorial/)

---

### Post by sapo on 2005-06-20
[QUOTE=mtron]So i think the panel should be made in C , with the gtk+ 2.0. 

I never worked with it, but this panel should not need  complex programming. Except, it would be nice to display the script status  in an embedded terminal, like synaptic does it, but for the beginning a basic interface with some buttons and tabs should do it

Is someone else interrested, who has some experience with gtk in programming the panel ?

If not, i'll try it, but it will take me some time to figure out the basics.

A good tutorial for gkt+ 2.0 that covers our needs for this small programm is [here](http://www.gtk.org/tutorial/)[/QUOTE]

Hum.. i think that it could be a dinamic, self-updating panel, like.. we upload all the scripts to some place, and when you open the program you click in refresh.. then it downloads all the new scripts.. 

We could make categories too.. and make a "template" script.. so anyone could help out with a script...

We could have a website to people upload the scripts, so some people could test it.. and then if it is good it could be added to the downloadable scripts  :grin: 

what do you guys think about it?

---

### Post by mtron on 2005-06-20
i re-wrote the Kurumin install script to use zenity dialogs.

This example can install or remove the package mp32ogg, with the trypical questions and package information. THe apt-get options allow unauthenticated installs and assume "yes" to every question.

Might be an "template" script.

```
#!/bin/sh
# zenity re-write of the Kurumin install script

## Here goes the package description
zenity --info \
       --text="Program Information: mp32ogg

Description: This is a small script to convert recursively your MP3 files and directory to Ogg Vorbis."
choice=`zenity --list --title "Convert mp3 to ogg files" --radiolist --column="Check" --column="description" "" "Install the program" "" "remove the program" "" "quit without a change"` 

## Install
if [ "$choice" = "Install the program" ];
then
zenity --question --text="Are you sure you wish to install?"
sudo apt-get -f install
sudo dpkg --configure -a
#replace mp32ogg with the package name
sudo apt-get -y --allow-unauthenticated install mp32ogg
sudo apt-get -f install

# post-install message and hint to man - pages
zenity --info \
       --text="install complete! 

for usage instructions type: 'man mp32ogg'"
fi

## Uninstall
if [ "$choice" = "remove the program" ];
then
zenity --warning \
          --text="Are you sure you wish to uninstall?"
#replace mp32ogg with the package name
sudo apt-get -y --purge remove mp32ogg
 zenity --info \
       --text="Uninstall complete!"
fi 

## Quit
if [ "$choice" = "quit without a change" ];
then
exit 0
fi

exit 0

```

---

### Post by mtron on 2005-06-20
[QUOTE=sapo]Hum.. i think that it could be a dinamic, self-updating panel, like.. we upload all the scripts to some place, and when you open the program you click in refresh.. then it downloads all the new scripts.. [/QUOTE]

Sounds great! but are you able to do it?

---

### Post by sapo on 2005-06-20
[QUOTE=mtron]i re-wrote the Kurumin install script to use zenity dialogs.

This example can install or remove the package mp32ogg, with the trypical questions and package information. THe apt-get options allow unauthenticated installs and assume "yes" to every question.

Might be an "template" script.
[/QUOTE]

Man.. i love you hehehe

it worked perfectly!  :grin: 

now we need to start adding more features.. and start thinking about a gui to handle it :D

i took a screenshot:
[[IMG]http://img213.echo.cx/img213/426/screenshot14nm.th.jpg[/IMG]](http://img213.echo.cx/my.php?image=screenshot14nm.jpg)

I was thinking about some features to put in the script...

we can make something to:
1 - make a backup of the sources.list
2 - create a new sources.list with the specific rep. where the program is
3 - apt-get update
4 - install the program
5 - restore the old sources.list

And maybe we can make a script to install some apps from CVS, like.. the script log into the cvs, download everything, compile, install and run the app  :grin:

---

### Post by sapo on 2005-06-20
[QUOTE=mtron]Sounds great! but are you able to do it?[/QUOTE]

i m not a linux programmer hehe i came up with the idea but i dont know exactly how to program.. btw i can try  :-# 

the website and interface to users upload the scripts and all that stuff i can program in php... but i ll need a little help with the other stuff  ](*,)

---

### Post by rubycon on 2005-06-20
[QUOTE=tread]Rubycon, could we see some screenshot or better yet, some code we could compile and test? It would be nice, and if you have a standard scripting interface we could start making scripts from the ubuntuguide already.[/QUOTE]
I will post the code completed so far later today, just need to brush it up a little so people can understand it ;)
For those who are curious about what i'm doing, take a look at the following xml example:
```

<Wizard>
	<Slide id="slide1" caption="This is a wizard" width="600" height="400">
		<Layout rows="10" cols="20">
			<Button id="next"     caption="Next" 	 top="9" left="16" bottom="10" right="20"/>
			<Button id="previous" caption="Previous" top="9" left="12" bottom="10" right="16"/>
			<Button id="cancel"   caption="Cancel"   top="9" left="8"  bottom="10" right="12"/>

			<RadioGroup id="group1">
				<Radio id="radio1" caption="Radio 1 label" top="2" left="2" bottom="3" right="7" value="true"/>
				<Radio id="radio2" caption="Radio 2 label" top="4" left="2" bottom="5" right="7" value="true"/>
			</RadioGroup>

			<Checkbox id="check1" caption="Checkbox 1 label" top="4" left="13" bottom="5" right="19" value="true"/>
		</Layout>
		<Callbacks>
			<OnButton id="Next">
				if ( radio1 == "true" ) then
					Execute("script1.sh")
					Change_Slide("slide2")
				else
					Execute("script2.sh")
					Change_Slide("slide3")
				end
			</OnButton>
			<OnButton id="Cancel">
				Quit()
			</OnButton>
		</Callbacks>
	</Slide>
</Wizard>

```
Then executed with my application this code builds a dialog window containing three buttons, two radiobuttons in group and one checkbox, all in GTK 2.0. So far the layout bit is about half done but the callbacks bit (where you call scripts etc) has to be done. Please let me know if this could be of any use. As mentioned before, I will post all the code later today for anyone interested.

---

### Post by mtron on 2005-06-20
So let's piont out where we wanna get (like i understood it so far)

1) create a panel control with three or more tabs, to preform various script run actions. the tabs could be software - Configuration - tweaking / tuning

Software tab: 
some basic tasks for all of them, like adding the extra & backport repositories to the sources, and update ubuntu, also a status icon would be nice, to show a user if the software is already installed. 

- colum for additional free software ( meaning GPL license), from the repos that are installed via scripts by clicking on the button

- colum for additional software ( non - free, e.g. acrobat, skype, RealPlayer ), from the repos that are installed via scripts by clicking on the button

- colum for software from 3rd party repositoreis (for e.g dvd - playback, some marrilant progs, beagle) and source to compile and / or install  by clicking on the button

Configuration tab:
- button for installing nvidia or ati display drivers
- use alsa sound architecture
- ect.

Tweaking:
- button to enable prelink
- some nautilus scripts
- disable some boot - up services (restet clock to gmt, etc.)
- ect

2) installing software
- a click on the button should call up a script (like the other one posted before) that installs (or compiles & installs) the software package automatically. after the script has finished, the user should come back to the panel, and a status icon should indicate, that this program is installed.

So what would be the best method to create this panel? How can i test the xml rubycon posted before? Is ist possible to dynamically update the panel, when new scripts are available?

---

### Post by sapo on 2005-06-20
mtron thanx for organizing everything.  :grin: 

There's a lot of things for us to talk about before start programing.. we need to have a way to check if the program is really installed.. for example:

I install the ati driver using the panel, but then i unistall it using synaptic.. how the panel is going to be updated?

And the panel should have an "output" like a terminal to show erros and other stuff, cause it isnt 100% of the scripts that are gonna run flawlessly.

Another thing that i was thinking about is that we can try to make some scripts to help newbies configure some stuff, like ip adress, screen resolution, etc.

we can make the panel using tabs, and make a list of available scripts in each tab, and the way you just organized them seens fine logical to me.

I think that the first thing is already started.. the templates to make the scripts, but we need some kind of template to make them ALL behave in the same way.

And we also need templates for all kinds of scripts, cvs, tarballs, .deb without reps, etc.

And also we need a simple way to translate the scripts to another language, give the credits to the authors, etc.

btw.. we have a lot to go.. but i think that the results will be worth all the work :grin:

---

### Post by mtron on 2005-06-20
[QUOTE=sapo] we need to have a way to check if the program is really installed.. for example:

I install the ati driver using the panel, but then i unistall it using synaptic.. how the panel is going to be updated?[/QUOTE]

for deb packages you can search for e.g. xmms and dump the result in a file
dpkg -l | grep xmms > output.txt

and later catch up the result with 
grep xmms output.txt

>  the panel should have an "output" like a terminal to show erros and other stuff, cause it isnt 100% of the scripts that are gonna run flawlessly.

Yes, that's absolutly needed, in Synapic package manager it works great

> Another thing that i was thinking about is that we can try to make some scripts to help newbies configure some stuff, like ip adress, screen resolution,

There are already very nice scrpts around in the forum, like parts of [this](http://www.ubuntuforums.org/showthread.php?t=37134) to do these jobs. 

So, Let's hope someone comes up with a good idea how to make the panel :-k

---

### Post by sapo on 2005-06-20
[QUOTE=mtron]for deb packages you can search for e.g. xmms and dump the result in a file
dpkg -l | grep xmms > output.txt

and later catch up the result with 
grep xmms output.txt



Yes, that's absolutly needed, in Synapic package manager it works great



There are already very nice scrpts around in the forum, like parts of [this](http://www.ubuntuforums.org/showthread.php?t=37134) to do these jobs. 

So, Let's hope someone comes up with a good idea how to make the panel :-k[/QUOTE]

Nice.. i was thinking about the panel here.. and as it is just scripts, we could make something like:

we have the folders like this:

scripts/software
scripts/hardware

And in these folders we just have to put the script.. so the panel can make a dinamic list, and inside each scripts we could have the informations about what the script does, who wrote it and all that stuff, so the panel will read the infos and show the scripts in the panel.

And when wil click in "update scripts" it just download the new scripts to the folders and update the old ones... then refresh the gui and you have a lot os scripts to install [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

btw i dont know how (and who) can we write the panel, wich language to use, etc.

Programmers.. where are you? we need advice  ](*,)

---

### Post by sapo on 2005-06-20
I ve found a script to install the nvidia driver and configure it in Kurumin, its a example that we could use:

```

#!/bin/sh 
# Script de instalação dos ícones mágicos 
# Escrito por Carlos E. Morimoto 

sudo-verificar 
if [ "$?" = "2" ]; then exit 0; fi 

export XDIALOG_HIGH_DIALOG_COMPAT=1 
DIALOG=Xdialog 
DIA=Xdialog 


clear 


IGNORE_CC_MISMATCH=yes 
IGNORE_CC_MISMATCH=1 

export IGNORE_CC_MISMATCH=yes 
export IGNORE_CC_MISMATCH=1 

cd /packages 

service kdm stop 
clear 


versaokernel=`uname -r` 


if [ $versaokernel = "2.6.8.1-kanotix-10" ] ; then 

tar -zxvf NVIDIA-Linux-x86-1.0-6111-pkg1.tar.gz 
cd NVIDIA-Linux-x86-1.0-6111-pkg1 
./nvidia-installer --accept-license 

else <----------------------------- incluido else 

if [ $versaokernel = "2.6.11-kanotix-7" ] ; then 

./NVIDIA-Linux-x86-1.0-7174-pkg1-custom.run --force-tls=classic --accept-license 


else 

./NVIDIA-Linux-x86-1.0-6629-pkg1.run --force-tls=classic --accept-license 

fi 
fi <------------------- incluido fi 

echo \alias char-major-195 nvidia >> /etc/modules.conf 
echo "echo \alias char-major-195 nvidia >> /etc/modules.conf" 
sleep 2 

echo \alias char-major-195 nvidia >> /etc/modutils/aliases 
echo "echo \alias char-major-195 nvidia >> /etc/modutils/aliases" 
sleep 2 

#update-modules 
#echo "update-modules" 
#sleep 2 

sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.old 
echo "sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.old" 
sleep 2 

clear 


# Cria o ícone para o nvidia-settings ## 

cd /home 

for i in * 
do 

rm -f /home/$i/Meu\ Computador/Configuração\ do\ driver\ nVidia 

echo '[Desktop Entry] 
Comment= 
Comment[pt_BR]= 
Encoding=UTF-8 
Exec=sudo-verificar; sudo nvidia-settings 
GenericName= 
GenericName[pt_BR]= 
Icon=mycomputer 
MimeType= 
Name=ConfiguraÃ§Ã£o do driver nVidia 
Name[pt_BR]=ConfiguraÃ§Ã£o do driver nVidia 
Path= 
StartupNotify=true 
Terminal=false 
TerminalOptions= 
Type=Application 
X-DCOP-ServiceType= 
X-KDE-SubstituteUID=false 
X-KDE-Username=' >> /home/$i/Meu\ Computador/Configuração\ do\ driver\ nVidia 

done 
##### 


T1="Instalar Drivers para Placas nVidia" 
M1="Se voce nao recebeu nenhuma mensagem de erro ate aqui, significa que os drivers estao corretamente instalados. 
Voce tem agora duas opcoes para editar o arquivo de configuracao do X.\n 
Posso tentar fazer as alteracoes necessarias automaticamente (yes) ou posso manter seu arquivo de configuracao 
inalterado para que voce faca as alteracoes descritas no artigo manualmente (no). 
Voce deseja que as alteracoes sejam feitas automaticamente?" 
$DIALOG --title "$T1" --yesno "$M1" 18 72 
x=$? 
if [ $x = 0 ] ; then 

rm -f /etc/X11/XF86Config-4nv 

sed -e 's/nvidia/nv/g' /etc/X11/XF86Config-4 > /etc/X11/XF86Config-4nv0 

sed -e 's/nv/nvidia/g' /etc/X11/XF86Config-4nv0 > /etc/X11/XF86Config-4nv1 
echo "Ativando driver: Localizando expressao *nv* e substituindo por *nvidia*"; sleep 1 

sed -e 's/fbdev/nvidia/g' /etc/X11/XF86Config-4nv1 > /etc/X11/XF86Config-4nv2 
echo "Ativando driver: Localizando expressao *fbdev* e substituindo por *nvidia*"; sleep 1 

sed -e 's/vesa/nvidia/g' /etc/X11/XF86Config-4nv2 > /etc/X11/XF86Config-4nv3 
echo "Ativando driver: Localizando expressao *vesa* e substituindo por *nvidia*"; sleep 1 

sed -e '\/Load\ \ "dri"/D' /etc/X11/XF86Config-4nv3 > /etc/X11/XF86Config-4nv4 
echo "Ativando driver: Removendo a linha *Load dri*"; sleep 1 

sed -e '\/Load\ \ "GLcore"/D' /etc/X11/XF86Config-4nv4 > /etc/X11/XF86Config-4nv5 
echo "Ativando driver: Removendo a linha *Load GLcore*"; sleep 1 

sed -e '\/Load\ \ "dbe"/D' /etc/X11/XF86Config-4nv5 > /etc/X11/XF86Config-4nv6 
echo "Ativando driver: Removendo a linha *Load dbe*"; sleep 1 

sed -e 's/\#\ DefaultColorDepth\ 16/\ DefaultColorDepth\ 16/g' /etc/X11/XF86Config-4nv6 > /etc/X11/XF86Config-4nv7 
echo "Descomentando a linha: DefaultColorDepth 16"; sleep 1 


rm -f /etc/X11/XF86Config-4 
mv /etc/X11/XF86Config-4nv7 /etc/X11/XF86Config-4 

rm -f /etc/X11/XF86Config-4nv* 

sleep 3 


T1="Instalar Drivers para Placas nVidia" 
M1="Caso algo de errado, voce pode recuperar suas configuracoes de video antigas rodando o comando:\n\n 
cp -f /etc/X11/XF86Config-4.old /etc/X11/XF86Config-4\n\n 
Anote este comando, voce pode precisar dele mais tarde." 
$DIALOG --title "$T1" --msgbox "$M1" 17 60 

T1="Instalar Drivers para Placas nVidia" 
M1="Nao tente me enganar  Eu sei que voce nao anotou. Vamos la, pegue um papel e uma caneta e escreva:\n\n 
cp -f /etc/X11/XF86Config-4.old /etc/X11/XF86Config-4\n" 
$DIALOG --title "$T1" --msgbox "$M1" 15 60 

T1="Instalar Drivers para Placas nVidia" 
M1="Tisc tisc... Apertou Enter de novo sem anotar? Que coisa mais feia... Vamos la, voce consegue. Ultima chance:\n\n 
cp -f /etc/X11/XF86Config-4.old /etc/X11/XF86Config-4\n" 
$DIALOG --title "$T1" --msgbox "$M1" 15 60 

fi 

if [ $x = 1 ] ; then 

T1="Instalar Drivers para Placas nVidia" 
M1="Por enquanto nao foi feita nenhuma modificacao na configuracao do video. Depois de concluir a instalacao o X sera 
reaberto ainda usando as configuracoes antigas. Edite o /etc/X11/XF86Config-4 fazendo as alteracoes manualmente e 
reinicie o modo grafico novamente para ativar o driver.\n\n 
" 
$DIALOG --title "$T1" --msgbox "$M1" 15 60 

fi 


T1="Instalar Drivers para Placas nVidia" 
M1="Voce gostaria de instalar tambem o Yanc? Ele e um configurador grafico que permite habilitar recursos como o Antialising, Vertex Shadding, 
TwinView, Saída de TV, etc. alem de fazer overclock na placa de video. Ao instala-lo sera criado um ícone no desktop. O download tem apenas 3 MB." 
$DIALOG --title "$T1" --yesno "$M1" 15 60 
x=$? 
if [ $x = 0 ] ; then 

cd /packages 
wget -c http://easynews.dl.sourceforge.net/sourceforge/yanc/yanc-0.2.1.tar.gz 
wget -c http://unc.dl.sourceforge.net/sourceforge/yanc/yanc-0.2.1.tar.gz 
wget -c http://umn.dl.sourceforge.net/sourceforge/yanc/yanc-0.2.1.tar.gz 

chmod 777 yanc-0.2.1.tar.gz 
cp yanc-0.2.1.tar.gz /usr/local/ 
cd /usr/local/ 
tar -zxvf yanc-0.2.1.tar.gz 
rm -f yanc-0.2.1.tar.gz 
cd yanc-0.2.1/ 
./install.sh 
cp /etc/skel-fix/yanc.desktop /home/$USER/Desktop/yanc.desktop 
cp /etc/skel-fix/yanc.desktop ~/Desktop/yanc.desktop 

apt-get install nvclock 
apt-get install nvclock-gtk 

fi 


T1="Instalar Drivers para Placas nVidia" 
M1="Voce gostaria de instalar tambem o nvtv? Ele permite habilitar e configurar a saida para TV em modelos 
que possuem este recurso. O Yanc tambem oferece esta opcao, mas as opções de configuracao do nvtv sao mais 
completas." 
$DIALOG --title "$T1" --yesno "$M1" 15 60 
x=$? 
if [ $x = 0 ] ; then 

sudo apt-get install nvtv/unstable 
cp /etc/skel-fix/nvtv.desktop /home/$USER/Desktop/nvtv.desktop 
chown kurumin.kurumin /home/kurumin/Desktop/nvtv.desktop 
cp /etc/skel-fix/nvtv.desktop ~/Desktop/nvtv.desktop 


fi 

echo "Concluindo a instalacao..." 

sleep 3 

sudo /etc/init.d/kdm start 



exit 0

```

And here a script that install NVU and create a desktop entry for it :D
```

#!/bin/sh

# Script de instalação dos ícones mágicos
#
# Script para instalar o NVU, originalmente escrito por dRoterdam
# Atualizado por Mango Jambo - ( mangojamboARROULBASSSbrturboPUUNTOcom )


case "`tty`" in
/dev/tty[1-8])
MODE=text
DIALOG=dialog
;;
/dev/pts/*|/dev/ttyp*)
MODE=x
export XDIALOG_HIGH_DIALOG_COMPAT=1
[ -x /usr/bin/gdialog ] && DIALOG=gdialog
[ -x /usr/bin/Xdialog ] && DIALOG=Xdialog
[ $DIALOG = dialog ] && MODE=text
;;
*)
esac


$DIALOG --title "UmClique" \
--backtitle " Instalar NVU " \
--radiolist "O NVU 0.90 é um editor html visual, desenvolvido com base no Mozilla Composer. O objetivo é
desenvolver um concorrente Open Source à altura do Dreanweaver\n
" 22 70 0 \
"Instalar" "Instalar e abrir o programa" off \
"Remover" "Remover o programa depois de instalado" off \
"Abrir" "Abrir o programa depois de instalado" off \
"Sair" "Sair sem fazer nada" off 2> /tmp/checklist.tmp.$$
retval=$?

if [ $retval = 1 ];
then
exit 0
fi

choice=`cat /tmp/checklist.tmp.$$`
rm -f /tmp/checklist.tmp.$$

# -----------------------------------

if [ "$choice" = "Instalar" ];
then


ICON=/packages/NVU.desktop
FILE="nvu-0.90-pc-linux2.6.10-gnu.tar.bz2"
PASTA="nvu-0.90"

sudo chmod +777 /packages
cd /packages

xterm -e wget -c http://cvs.nvu.com/download/$FILE

sudo rm -Rf /usr/local/nvu*
sudo rm -f /usr/local/bin/nvu

sudo cp $FILE /usr/local
cd /usr/local
sudo tar -jxvf $FILE
sudo rm -f $FILE

sudo ln -s /usr/lib/libstdc++.so.5 libstdc++.so.3

sudo ln -sf /usr/local/$PASTA/nvu /usr/local/bin/nvu


# criar ícone de atalho no menu do KDE
cat >> /packages/NVU.desktop << EOF
[Desktop Entry]
Encoding=UTF-8
Exec=/usr/local/nvu-0.90/nvu
GenericName=Editor HTML
GenericName[pt_BR]=Editor HTML Visual
Icon=/usr/local/nvu-0.90/icons/mozicon50.xpm
Name[pt_BR]=NVU
Type=Application
X-KDE-SubstituteUID=false
EOF

sudo cp $ICON /usr/share/applnk/Internet/


$DIALOG --left --title "$T" --beep --yesno "Deseja adicionar um ícone na Área de Trabalho ?" 0 0

case $? in
0)
cp /packages/NVU.desktop $HOME/Desktop/
/usr/local/$PASTA/nvu ;;
1)
/usr/local/$PASTA/nvu ;;
255)
/usr/local/$PASTA/nvu ;;
esac

sleep 8



fi

# -----------------------------------

if [ "$choice" = "Remover" ];
then

sudo rm -rf /usr/local/$PASTA
sudo rm -f /usr/local/bin/nvu
sudo rm -f /usr/share/applnk/Internet/NVU.desktop
sleep 5


fi

# -----------------------------------


if [ "$choice" = "Abrir" ];
then

nvu

fi

# -----------------------------------

if [ "$choice" = "Sair" ];
then

exit 0

fi



exit

```

---

### Post by phen on 2005-06-20
Hello!

Just got an idea for a script:

automatic checking harddisks and cdroms for DMA compatibility and turning it on.

this task is not very easy, but absolutely necessary to use ubuntu as a windows replacement (that is what it will be for many people using your scipts), therefore, a script would be nice!

good idea by the way!

and my two cents about the mp3/flash and OSS problem: By making installing of mp3 and flash and ati/nvidia drivers easy, more people will convert to an OS like linux. this could help open source progress. Just think about the people using  an handheld mp3 player! it is NOT an OGG player! Without mp3 support, i would not be able to use linux. making linux more popular will probably end up in some OGG players being sold in stores. i will by one - but for now, an easy installation of mp3 is necessary. (please note: i still think that it should not be shipped out of the box, because it will make people aware of the non-free situation!)


cheers,

kai

---

### Post by rubycon on 2005-06-20
Ok now I've finally put up my work so far on the wizard program. Right now you are able to create a dialog and fill it with buttons, checkboxes and radiobuttons. More to come soon. The program can't do anything usefull yet, however, since the callbacks have not been implemented yet. But anyone who is curious can try it out here:

[http://www.dtek.chalmers.se/~anderssb/wizard/](http://www.dtek.chalmers.se/~anderssb/wizard/)

Once compiled you can try it out by executing the program with the sample xml file (wizard.xml) as argument.

---

### Post by sapo on 2005-06-21
[QUOTE=phen]Hello!

Just got an idea for a script:

automatic checking harddisks and cdroms for DMA compatibility and turning it on.

this task is not very easy, but absolutely necessary to use ubuntu as a windows replacement (that is what it will be for many people using your scipts), therefore, a script would be nice!

good idea by the way!

and my two cents about the mp3/flash and OSS problem: By making installing of mp3 and flash and ati/nvidia drivers easy, more people will convert to an OS like linux. this could help open source progress. Just think about the people using  an handheld mp3 player! it is NOT an OGG player! Without mp3 support, i would not be able to use linux. making linux more popular will probably end up in some OGG players being sold in stores. i will by one - but for now, an easy installation of mp3 is necessary. (please note: i still think that it should not be shipped out of the box, because it will make people aware of the non-free situation!)


cheers,

kai[/QUOTE]


Yes..thats the point.. i have a Sony mp3 player in my car, it plays just mp3, dont plays wma or another format... why the hell am i going to convert my mp3 to ogg?

---

### Post by sapo on 2005-06-21
[QUOTE=rubycon]Ok now I've finally put up my work so far on the wizard program. Right now you are able to create a dialog and fill it with buttons, checkboxes and radiobuttons. More to come soon. The program can't do anything usefull yet, however, since the callbacks have not been implemented yet. But anyone who is curious can try it out here:

[http://www.dtek.chalmers.se/~anderssb/wizard/](http://www.dtek.chalmers.se/~anderssb/wizard/)

Once compiled you can try it out by executing the program with the sample xml file (wizard.xml) as argument.[/QUOTE]

i l compiling it and will post a feedback soon, but please when adding files to a tar.gz archieve just put then all in a folder... it messed up all my home folder when i extracted it  ](*,)

---

### Post by mtron on 2005-06-21
i thought a bit about the panel (dynamic integration ect,) and i think the best idea is to use existing technology already used by ubuntu.

What i am talking about is the [WinFOSS](https://wiki.ubuntu.com/WinFOSS) open source install interface used in the Ubuntu Live CD for Windows software, so why not using the same system for a ubuntu install helper?

It semms that  canocial also [sponsors](http://www.canonical.com/projects/theopencd)  the [opencd project](http://www.theopencd.org/)  who developed this script. there is a thread about it [here](http://ubuntuforums.org/showthread.php?t=18709) . 

[Henrik](http://ubuntuforums.org/member.php?userid=143) , a developer, semms to be the preson to talk to. i'll mail him, and see what he thinks about it.

Does sb. have a live-cd to see the browser in action, and get to the source to post it here?

---

### Post by rubycon on 2005-06-22
[QUOTE=sapo]i l compiling it and will post a feedback soon, but please when adding files to a tar.gz archieve just put then all in a folder... it messed up all my home folder when i extracted it  ](*,)[/QUOTE]

Sorry about that. Hate it when others forget it and then I do it myself. Shame on me. Anyway, it has been corrected now. Looking forward to some feedback.

---

### Post by sapo on 2005-06-22
[QUOTE=rubycon]Sorry about that. Hate it when others forget it and then I do it myself. Shame on me. Anyway, it has been corrected now. Looking forward to some feedback.[/QUOTE]

It woking as it was supposed to do.. looking forward to some new implementations and a manual to how to write the xml file...  :grin:

---

### Post by sapo on 2005-06-22
[QUOTE=mtron]i thought a bit about the panel (dynamic integration ect,) and i think the best idea is to use existing technology already used by ubuntu.

What i am talking about is the [WinFOSS](https://wiki.ubuntu.com/WinFOSS) open source install interface used in the Ubuntu Live CD for Windows software, so why not using the same system for a ubuntu install helper?

It semms that  canocial also [sponsors](http://www.canonical.com/projects/theopencd)  the [opencd project](http://www.theopencd.org/)  who developed this script. there is a thread about it [here](http://ubuntuforums.org/showthread.php?t=18709) . 

[Henrik](http://ubuntuforums.org/member.php?userid=143) , a developer, semms to be the preson to talk to. i'll mail him, and see what he thinks about it.

Does sb. have a live-cd to see the browser in action, and get to the source to post it here?[/QUOTE]

Hum.. it looks like a good interface, but isnt it for windows? or is there some way to modify it.. or are we going to just make a similar interface? i ve started to learn with python..

but i think that we could gatter all the interested people in doing this and start a more organize project than just talking about it..

What do you think about a mainling list or maybe a forum?

Whats the requirements to have a sub-forum in the 3rd party projects?

---

### Post by mtron on 2005-06-22
hi sapo! 

seems we are the only one interrested in it (for now)..

Never mind. I have also some python knowledge, and programmed a small browser interface, like Winfoss uses for windows. 

The python browser uses the gtkmozembed widget, and might be quite dependency heavy for a new install (it might need the mozilla suite & the python stuff - i know, not good, but something to start with) Can you check it out?

it's a very basic interface, just with a foward & back button and loads a standard defined page (in the example it loads gnomefiles) 

For the developmend i also integrated a adress bar & go button. if you wanna use it, just delete all ## in the script.

So what i was thinking about:

we create a tgz archive with the scripts & description of the programs, and on install it unpacks it in a local directory (e.g. under $HOME\installhelper) when the user opens the browser it takes him to the local files. He can click through our script acrive and launch the scripts by clicking on a "install" button. 

On the windows cd they link the install button with an file named "Installer.Ich" the command to launch the app is:

```
[Launch] 
ExecuteFile=${cwd}\..\programs\abiword\abiword-setup-2.2.5.exe 
```

you can't launch a file (or script) in linux this way, but i am sure there is a possibility to launch a script (or terminal) in Linux also.

But one after the other. First to start. here is the python browser. Can you test it & the needed dependencies? 

```
#!/usr/bin/python
# Small Install Helper browser Window v.0.1
# to activate adress bar, delete all ##

import os
import sys
import gtk
import gtkmozembed

#setting calss & window position
class SIHBrowser:
	def __init__(self, URL = "http://www.gnomefiles.org/", parent = None):		
		if parent == None:
			self.parent = gtk.Window(gtk.WINDOW_TOPLEVEL)
			self.parent.set_border_width(10)
			self.parent.set_position(gtk.WIN_POS_CENTER_ALWAYS)
			self.parent.set_default_size(802, 602)		
		else:
			self.parent = parent
		
		# Initialize the widgets...
		self.widget = gtkmozembed.MozEmbed()
		self.vbox = gtk.VBox(False, 5)
		self.hbox = gtk.HBox(False, 5)
		##self.entry = gtk.Entry(256)
		##self.button = gtk.Button("Go")
		self.back = gtk.Button(stock=gtk.STOCK_GO_BACK)
		self.forward = gtk.Button(stock=gtk.STOCK_GO_FORWARD)
		
		# Arrange them...
		self.hbox.pack_start(self.back, expand=False, padding=2)
		self.hbox.pack_start(self.forward, expand=False, padding=2)
		##self.hbox.pack_start(self.entry, expand=True, padding=5)
		##self.hbox.pack_start(self.button, expand=False, padding=2)
		self.vbox.pack_start(self.hbox, expand=False, padding=5)
		self.vbox.pack_start(self.widget)
		
		# Connect signals
		##self.widget.connect("location", self.on_location_changed)
		##self.button.connect("clicked", self.on_entry_changed)
		##self.entry.connect('key_press_event', self.on_key_press)
		self.forward.connect("clicked", self.on_forward)
		self.back.connect("clicked", self.on_back)
		
		
		self.parent.add(self.vbox)
		
		if URL != None:
			self.widget.load_url(URL)
		
		self.parent.show_all()
	
			
	def on_forward(self, data = None):
		self.widget.go_forward()
	
	def on_back(self, data = None):
		self.widget.go_back()
	
	##def on_location_changed(self, data):
		##self.entry.set_text(self.widget.get_location())
	
	##def on_entry_changed(self, data = None):
		##self.widget.load_url(self.entry.get_text())

	##def on_key_press(self, widget, event, *args):
		##if event.keyval == gtk.keysyms.Return:
			##self.on_entry_changed()
		


def __windowExit(widget, data=None):
	gtk.main_quit()
	
if __name__ == "__main__":


	window = SIHBrowser()
	window.parent.connect("destroy", __windowExit)
	gtk.main()


```

---

### Post by sapo on 2005-06-22
mtron, it worked perfectly here... but these dependencies are a problem...

I was thinking here.. if we could make it execute the script when you click in the link inside the program... like, it download the script to a temp folder and execute it..

In this way we could make a website with all the scripts, when someone open the app the site opens, and then he get a lot of scripts.. when he clicks it is installed or unistalled... btw.. i dont know if its a good ideia..

i ll try to learn more about python.. i think that it souldnt be that hard do code  ](*,)

---

### Post by mtron on 2005-06-27
Hi sapo! 

[QUOTE=sapo] i think that it souldnt be that hard do code[/QUOTE]

I saw you worked on the python way,. Good luck! I gave up the python browser due to the dependencies...

 well i used now a different approach and started programming with good old C++ & glade a very basic gtk interface 

Requirements:
- build-essentials
- automake
- libgnomeui-dev

Install:
- Unpack sih_v0.1.tar.gz to a temp directory (e.g. $HOME/test)
- cd to the unpacked source and run "./configure" and "make" (don't run a make install till now)
- now cd to "src" and run the app with "./sih" or "gksudo ./sih" if you want to test a install script

you need also the scripts-package "sih_scripts_v0.1.tar.gz". create a directory /usr/share/sih and unpack the scripts to this folder (don't forget to check the permissions!)

Well, i started programming 5 days ago, so any feedback & suggestions are more than welcome. Also if a real programmer thinks that this is very bad work please feel free to improve it, or write a better gui ( that's my secret intention  ;-)  ) 

Next thing to do is attach a terminal to the gui, where the status of the script is shown..

---

### Post by sapo on 2005-06-27
[QUOTE=mtron]Hi sapo! 



I saw you worked on the python way,. Good luck! I gave up the python browser due to the dependencies...

 well i used now a different approach and started programming with good old C++ & glade a very basic gtk interface 

Requirements:
- build-essentials
- automake
- libgnomeui-dev

Install:
- Unpack sih_v0.1.tar.gz to a temp directory (e.g. $HOME/test)
- cd to the unpacked source and run "./configure" and "make" (don't run a make install till now)
- now cd to "src" and run the app with "./sih" or "gksudo ./sih" if you want to test a install script

you need also the scripts-package "sih_scripts_v0.1.tar.gz". create a directory /usr/share/sih and unpack the scripts to this folder (don't forget to check the permissions!)

Well, i started programming 5 days ago, so any feedback & suggestions are more than welcome. Also if a real programmer thinks that this is very bad work please feel free to improve it, or write a better gui ( that's my secret intention  ;-)  ) 

Next thing to do is attach a terminal to the gui, where the status of the script is shown..[/QUOTE]

nice.. the app worked!  :grin: 

btw.. i was thinking about a little different interface.. 

something like this:
[http://www.grawert.net/services.png](http://www.grawert.net/services.png)

with the names and a red or green dot.. installed and uninstalled...

cause imagine if we reach a very high number of scripts.. it isnt going to fit in the screen.. 

It is something like synaptic.. you mark and the install or unistall.. 

btw.. nice work ^^

---

### Post by mtron on 2005-06-28
[QUOTE=sapo]with the names and a red or green dot.. installed and uninstalled...[/QUOTE]

I already tried it, but i could not figure it out. i will set it on the todo list... 
I have a very busy day 2day in the office, but when i come home i'll try it.

Edit: ok i looked now at the pic you posted. Very interresting. We could make groups on the hardcored gtk interface, like audio tools, video tools, codecs ect, and when you click on a button it launches a zenity checklist where the user can choose the apps to install. 

With this way, we can also update the scripts very easy,without changing the gtk interface. 

But a problem is when new users don't know that e.g xmms is Winamp - like. So you need also a help button, where the packages are explained. (could also be done by a script, or a gnome helpfile?

---

### Post by tread on 2005-06-28
Hey guys, 
I'm sorry .. I showed a lot of interest and then vanished .. fact is, I've been snowed under work at the moment :( and will continue to be for a month. This thread is on my subscribed threads list, I'll come back then and offer my services. Till then, all the best!

---

### Post by mtron on 2005-07-08
Just to keep you updated. I worked on my little proggie during the last days until i discovered this 

[http://niran.org/code/soc/](http://niran.org/code/soc/)

Well, this is pretty much what i wanted to do, so there is not really a use for my app. Anyway. It was a nice learning process...

---

### Post by sapo on 2005-07-08
[QUOTE=mtron]Just to keep you updated. I worked on my little proggie during the last days until i discovered this 

[http://niran.org/code/soc/](http://niran.org/code/soc/)

Well, this is pretty much what i wanted to do, so there is not really a use for my app. Anyway. It was a nice learning process...[/QUOTE]

that is sad for you but.. i think that this project is awesome and we hope we can make a good use for it.. btw..

why dont you change your project into a "install helper" to make some scripts to help installing and configuring some devices..

---

