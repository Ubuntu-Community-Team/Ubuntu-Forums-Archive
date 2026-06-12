---
title: "build script automatically kernel 3.3.5"
date: 2012-05-11
forum: Tutorials
---

### Post by 4d4c47 on 2012-05-11
build script automatically kernel 3.3.7 for ubuntu 11.10 64 BITS:


Page project:

[http://sourceforge.net/projects/scriptkernel/](http://sourceforge.net/projects/scriptkernel/)


```

#!/bin/bash

# script PARA USUARIOS DO UBUNTU 11.10 baixa e compila kernel tudo automaticamente CRIADO PELOS USUÁRIOS DO FORUM UBUNTU BR:
# http://ubuntuforum-br.org/index.php/topic,95318.0.html
#
#
# http://ubuntuforum-br.org/index.php/topic,29799.3960.html
#
#
# Pagina do projeto:
#
# http://sourceforge.net/projects/scriptkernel/
#
# totalmente GPL-3
#
# 
#
# 
# script de compilação do kernel 3.3.X para uso no ubuntu 11.10 64 bits, 
# baixa tudo automaticamente (dependências, compiladores, 
# kernel e patchs) com patch 3.3.0-ck1(BFS) + BFQ   e usando cflag -march=native + -Ofast.
#
# para usa-lo salve ele com o nome de scriptkernel e para executa-lo, utilize um terminal MAXIMIZADO e execute:
#
# $ time sudo bash scriptkernel
#
# e em 2 minutos aparecerá uma tela do menuconfig, 
# escolha a sua arquitetura de seu processador na parte PROCESSOR TYPE AND FEATURES e depois clicke em EXIT e em YES,  
# e logo começará a compilação e no final a instalação automatica.
#
# OBS= para maior exito na compilação (certeza que irá ser executado sem erros) 
# deve ter em seu PC ou NOTEBOOK no mínimo de 2 GB de RAM e ter pelo menos 15 GB livre
# em seu disco rígido (não é uma regra, mas evita de erro por falta de espaço no disco)
#
#
####################################################################################################################################
#
#
# English translation:
#
# Script FOR USERS OF UBUNTU 11.10 low and kernel compiles everything automatically CREATED BY USERS OF THE FORUM BR UBUNTU:
# http://ubuntuforum-br.org/index.php/topic,95318.0.html
#
#
# http://ubuntuforum-br.org/index.php/topic,29799.3960.html
#
#
# http://sourceforge.net/projects/scriptkernel/
#
# Fully GPL-3
#
#
#
#
# Build script for use in kernel 3.X ubuntu 11.10 64 bit
# Low everything automatically (dependencies, compilers,
# Kernel and patches) with patch 3.3.0-ck1(BFS) + BFQ and cflag using -march=native + -Ofast.
#
# Use it to save it with the name of scriptkernel and run it, use a maximized terminal and run:
#
# $ time sudo bash scriptkernel
#
# 2 minutes and a screen of menuconfig,
# Choose the architecture of your processor in the "Processor type and features" and then clicke "EXIT" and "YES",
# And will soon begin to build and end the installation automatically.
#
# OBS = for greater success in the compilation (make sure it will run without errors)
# Must have on your PC or NOTEBOOK at least 2 GB of RAM and at least 15 GB free
# On your hard drive (not a rule but avoids error due to lack of disk space)
#
#
############################################################################################################################################



############################################
#vc só vai ter o trabalho de editar aqui:

#versão do kernel a ser compilado
kernel=3.3

#path de atualização
patchkernel=3.3.7

#patch BFQ
bfq=3.3.0-v3r3


#patch ck
patchck=3.3-ck1

#sufixo
ckk=ck1


#.config antigo
kernelantigo=atual

############################################

# não precisa mexer em mais nada aqui

##################################
#arquitetura: amd64 ou i386
arqt=$(dpkg --print-architecture)


#CL=CONCURRENCY_LEVEL do processador
CL=$(grep -c processor /proc/cpuinfo)
##################################

########baixando compiladores e dependencias########################################################
sudo apt-get update
sudo apt-get install kernel-package gcc-4.6 libncurses5 libncurses5-dev build-essential patch -y
####################################################################################################



######deletando patchs antigos#############
sudo rm /usr/src/patch-$patchkernel
sudo rm /usr/src/patch-$patchck
sudo rm /usr/src/0001-base-packaging.patch
sudo rm /usr/src/0002-debian-changelog.patch
sudo rm /usr/src/0003-default-configs.patch
sudo rm /usr/src/0001-block-cgroups-kconfig-build-bits-for-BFQ-v3r3-3.3.patch
sudo rm /usr/src/0002-block-introduce-the-BFQ-v3r3-I-O-sched-for-3.3.patch
############################################




cd /usr/src
wget -c http://www.kernel.org/pub/linux/kernel/v3.x/linux-$kernel.tar.bz2


sudo tar -jxpvf /usr/src/linux-$kernel.tar.bz2
sudo mv /usr/src/linux-$kernel /usr/src/linux-$patchkernel-$ckk


wget -c http://www.kernel.org/pub/linux/kernel/v3.x/patch-$patchkernel.bz2
wget -c http://ck.kolivas.org/patches/3.0/$kernel/$patchck/patch-$patchck.bz2
wget -c http://algo.ing.unimo.it/people/paolo/disk_sched/patches/$bfq/0001-block-cgroups-kconfig-build-bits-for-BFQ-v3r3-3.3.patch
wget -c http://algo.ing.unimo.it/people/paolo/disk_sched/patches/$bfq/0002-block-introduce-the-BFQ-v3r3-I-O-sched-for-3.3.patch



#ubuntu patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-precise/0001-base-packaging.patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-precise/0002-debian-changelog.patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-precise/0003-default-configs.patch



sudo bunzip2 /usr/src/patch-$patchkernel.bz2
sudo bunzip2 /usr/src/patch-$patchck.bz2


cd /usr/src/linux-$patchkernel-$ckk

sudo patch -p1 < /usr/src/patch-$patchkernel
sudo patch -p1 < /usr/src/patch-$patchck
sudo patch -p1 < /usr/src/0001-block-cgroups-kconfig-build-bits-for-BFQ-v3r3-3.3.patch
sudo patch -p1 < /usr/src/0002-block-introduce-the-BFQ-v3r3-I-O-sched-for-3.3.patch
sudo patch -p1 < /usr/src/0001-base-packaging.patch
sudo patch -p1 < /usr/src/0002-debian-changelog.patch
sudo patch -p1 < /usr/src/0003-default-configs.patch


######################
#sudo cp /boot/config-$kernelantigo /usr/src/linux-$patchkernel-$ckk/.config

config_file=$(locate /boot/config-* | sort -r | head -1)

sudo cp $config_file /usr/src/linux-$patchkernel-$ckk

#########################

#sudo gedit Makefile  

sleep 3

sudo make menuconfig

sudo sed 's/CONFIG_RTS5139=m/# CONFIG_RTS5139 is not set/g' /usr/src/linux-$patchkernel-$ckk/.config > /usr/src/linux-$patchkernel-$ckk/cc && mv /usr/src/linux-$patchkernel-$ckk/cc /usr/src/linux-$patchkernel-$ckk/.config

sleep 3

############ script do grande Stivekx #######################

#!/bin/bash

#Script para automatizar a mudança das flags na hora de compilar o kernel.
#Mais informações sobre como compilar o kernel para seu processador:
#http://ubuntuforum-br.org/index.php/topic,81718.0.html

#Modo de usar:
#Após baixar o kernel, descompactar, criar um link simbólico para ele no /usr/src/linux:
# cd /usr/src/linux    
# sudo su
# chmod +x script.sh
# ./script.sh
#O script deve ser executado como root. Recomendo que use sudo su - e rode o script ao invés de sudo sh script.sh


#Script criado por André Steinn

#Aqui é a lista de arquivos que ele vai dar replace no -march= por -march=native. Você pode mudar essa lista de arquivos passando a lista pela opção a e separados pro virgula
#e.g.: ./script.sh -a arch/x86/boot/compressed/Makefile,arch/x86/boot/Makefile,arquivo1,arquivo2,arquivo3

arquivos=( "arch/x86/boot/compressed/Makefile" "arch/x86/boot/Makefile" "arch/x86/kernel/acpi/realmode/Makefile" "arch/x86/Kconfig.cpu" "arch/x86/Makefile" "arch/x86/Makefile_32.cpu")

#Aqui eu verifico se a pessoa passou algum argumento na hora de executar o script
while getopts ":a:c" opt; do
  case $opt in
    a)
      echo "Você setou uma lista de arquivos personalizada: $OPTARG" >&2
    IFS=',' read -ra arquivos <<< "$OPTARG"
      ;;
    \?)
      echo "Opção inválida: -$OPTARG" >&2
      exit 1
      ;;
  esac
done

#Aqui eu faço um loop e altero os arquivos, removendo o -march=() por -march=native
for i in "${arquivos[@]}"
do
    echo "Path no arquivo:"$i
    sed -e 's/-march=\([A-Z0-9a-z]\+\)/-march=native -Ofast/g'  $i > "$i.file_changed"
    mv "$i.file_changed" $i
done



################

sleep 3


#time sudo CONCURRENCY_LEVEL=2 make-kpkg --initrd kernel_image kernel_headers modules_image

time sudo CONCURRENCY_LEVEL=$CL make-kpkg --initrd kernel_image kernel_headers modules_image


cd /usr/src
sudo dpkg -i linux-image-$patchkernel-$ckk\_$patchkernel-$ckk-10.00.Custom_$arqt.deb linux-headers-$patchkernel-$ckk\_$patchkernel-$ckk-10.00.Custom_$arqt.deb

sleep 3

cd /lib/modules
sudo mkinitramfs -o /boot/initrd.img-$patchkernel-$ckk $patchkernel-$ckk
sudo update-grub

sleep 5
echo 'tudo belezinha'


```download is install BFS + BFQ + UBUNTU PATCHS + CFLAGS -march=native -Ofast

---

### Post by 4d4c47 on 2012-08-21
> **4d4c47 said:**
> build script automatically kernel 3.3.7 for ubuntu 11.10 64 BITS:


Page project:

[http://sourceforge.net/projects/scriptkernel/](http://sourceforge.net/projects/scriptkernel/)


```

#!/bin/bash

# script PARA USUARIOS DO UBUNTU 11.10 baixa e compila kernel tudo automaticamente CRIADO PELOS USUÁRIOS DO FORUM UBUNTU BR:
# http://ubuntuforum-br.org/index.php/topic,95318.0.html
#
#
# http://ubuntuforum-br.org/index.php/topic,29799.3960.html
#
#
# Pagina do projeto:
#
# http://sourceforge.net/projects/scriptkernel/
#
# totalmente GPL-3
#
# 
#
# 
# script de compilação do kernel 3.3.X para uso no ubuntu 11.10 64 bits, 
# baixa tudo automaticamente (dependências, compiladores, 
# kernel e patchs) com patch 3.3.0-ck1(BFS) + BFQ   e usando cflag -march=native + -Ofast.
#
# para usa-lo salve ele com o nome de scriptkernel e para executa-lo, utilize um terminal MAXIMIZADO e execute:
#
# $ time sudo bash scriptkernel
#
# e em 2 minutos aparecerá uma tela do menuconfig, 
# escolha a sua arquitetura de seu processador na parte PROCESSOR TYPE AND FEATURES e depois clicke em EXIT e em YES,  
# e logo começará a compilação e no final a instalação automatica.
#
# OBS= para maior exito na compilação (certeza que irá ser executado sem erros) 
# deve ter em seu PC ou NOTEBOOK no mínimo de 2 GB de RAM e ter pelo menos 15 GB livre
# em seu disco rígido (não é uma regra, mas evita de erro por falta de espaço no disco)
#
#
####################################################################################################################################
#
#
# English translation:
#
# Script FOR USERS OF UBUNTU 11.10 low and kernel compiles everything automatically CREATED BY USERS OF THE FORUM BR UBUNTU:
# http://ubuntuforum-br.org/index.php/topic,95318.0.html
#
#
# http://ubuntuforum-br.org/index.php/topic,29799.3960.html
#
#
# http://sourceforge.net/projects/scriptkernel/
#
# Fully GPL-3
#
#
#
#
# Build script for use in kernel 3.X ubuntu 11.10 64 bit
# Low everything automatically (dependencies, compilers,
# Kernel and patches) with patch 3.3.0-ck1(BFS) + BFQ and cflag using -march=native + -Ofast.
#
# Use it to save it with the name of scriptkernel and run it, use a maximized terminal and run:
#
# $ time sudo bash scriptkernel
#
# 2 minutes and a screen of menuconfig,
# Choose the architecture of your processor in the "Processor type and features" and then clicke "EXIT" and "YES",
# And will soon begin to build and end the installation automatically.
#
# OBS = for greater success in the compilation (make sure it will run without errors)
# Must have on your PC or NOTEBOOK at least 2 GB of RAM and at least 15 GB free
# On your hard drive (not a rule but avoids error due to lack of disk space)
#
#
############################################################################################################################################



############################################
#vc só vai ter o trabalho de editar aqui:

#versão do kernel a ser compilado
kernel=3.3

#path de atualização
patchkernel=3.3.7

#patch BFQ
bfq=3.3.0-v3r3


#patch ck
patchck=3.3-ck1

#sufixo
ckk=ck1


#.config antigo
kernelantigo=atual

############################################

# não precisa mexer em mais nada aqui

##################################
#arquitetura: amd64 ou i386
arqt=$(dpkg --print-architecture)


#CL=CONCURRENCY_LEVEL do processador
CL=$(grep -c processor /proc/cpuinfo)
##################################

########baixando compiladores e dependencias########################################################
sudo apt-get update
sudo apt-get install kernel-package gcc-4.6 libncurses5 libncurses5-dev build-essential patch -y
####################################################################################################



######deletando patchs antigos#############
sudo rm /usr/src/patch-$patchkernel
sudo rm /usr/src/patch-$patchck
sudo rm /usr/src/0001-base-packaging.patch
sudo rm /usr/src/0002-debian-changelog.patch
sudo rm /usr/src/0003-default-configs.patch
sudo rm /usr/src/0001-block-cgroups-kconfig-build-bits-for-BFQ-v3r3-3.3.patch
sudo rm /usr/src/0002-block-introduce-the-BFQ-v3r3-I-O-sched-for-3.3.patch
############################################




cd /usr/src
wget -c http://www.kernel.org/pub/linux/kernel/v3.x/linux-$kernel.tar.bz2


sudo tar -jxpvf /usr/src/linux-$kernel.tar.bz2
sudo mv /usr/src/linux-$kernel /usr/src/linux-$patchkernel-$ckk


wget -c http://www.kernel.org/pub/linux/kernel/v3.x/patch-$patchkernel.bz2
wget -c http://ck.kolivas.org/patches/3.0/$kernel/$patchck/patch-$patchck.bz2
wget -c http://algo.ing.unimo.it/people/paolo/disk_sched/patches/$bfq/0001-block-cgroups-kconfig-build-bits-for-BFQ-v3r3-3.3.patch
wget -c http://algo.ing.unimo.it/people/paolo/disk_sched/patches/$bfq/0002-block-introduce-the-BFQ-v3r3-I-O-sched-for-3.3.patch



#ubuntu patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-precise/0001-base-packaging.patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-precise/0002-debian-changelog.patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-precise/0003-default-configs.patch



sudo bunzip2 /usr/src/patch-$patchkernel.bz2
sudo bunzip2 /usr/src/patch-$patchck.bz2


cd /usr/src/linux-$patchkernel-$ckk

sudo patch -p1 < /usr/src/patch-$patchkernel
sudo patch -p1 < /usr/src/patch-$patchck
sudo patch -p1 < /usr/src/0001-block-cgroups-kconfig-build-bits-for-BFQ-v3r3-3.3.patch
sudo patch -p1 < /usr/src/0002-block-introduce-the-BFQ-v3r3-I-O-sched-for-3.3.patch
sudo patch -p1 < /usr/src/0001-base-packaging.patch
sudo patch -p1 < /usr/src/0002-debian-changelog.patch
sudo patch -p1 < /usr/src/0003-default-configs.patch


######################
#sudo cp /boot/config-$kernelantigo /usr/src/linux-$patchkernel-$ckk/.config

config_file=$(locate /boot/config-* | sort -r | head -1)

sudo cp $config_file /usr/src/linux-$patchkernel-$ckk

#########################

#sudo gedit Makefile  

sleep 3

sudo make menuconfig

sudo sed 's/CONFIG_RTS5139=m/# CONFIG_RTS5139 is not set/g' /usr/src/linux-$patchkernel-$ckk/.config > /usr/src/linux-$patchkernel-$ckk/cc && mv /usr/src/linux-$patchkernel-$ckk/cc /usr/src/linux-$patchkernel-$ckk/.config

sleep 3

############ script do grande Stivekx #######################

#!/bin/bash

#Script para automatizar a mudança das flags na hora de compilar o kernel.
#Mais informações sobre como compilar o kernel para seu processador:
#http://ubuntuforum-br.org/index.php/topic,81718.0.html

#Modo de usar:
#Após baixar o kernel, descompactar, criar um link simbólico para ele no /usr/src/linux:
# cd /usr/src/linux    
# sudo su
# chmod +x script.sh
# ./script.sh
#O script deve ser executado como root. Recomendo que use sudo su - e rode o script ao invés de sudo sh script.sh


#Script criado por André Steinn

#Aqui é a lista de arquivos que ele vai dar replace no -march= por -march=native. Você pode mudar essa lista de arquivos passando a lista pela opção a e separados pro virgula
#e.g.: ./script.sh -a arch/x86/boot/compressed/Makefile,arch/x86/boot/Makefile,arquivo1,arquivo2,arquivo3

arquivos=( "arch/x86/boot/compressed/Makefile" "arch/x86/boot/Makefile" "arch/x86/kernel/acpi/realmode/Makefile" "arch/x86/Kconfig.cpu" "arch/x86/Makefile" "arch/x86/Makefile_32.cpu")

#Aqui eu verifico se a pessoa passou algum argumento na hora de executar o script
while getopts ":a:c" opt; do
  case $opt in
    a)
      echo "Você setou uma lista de arquivos personalizada: $OPTARG" >&2
    IFS=',' read -ra arquivos <<< "$OPTARG"
      ;;
    \?)
      echo "Opção inválida: -$OPTARG" >&2
      exit 1
      ;;
  esac
done

#Aqui eu faço um loop e altero os arquivos, removendo o -march=() por -march=native
for i in "${arquivos[@]}"
do
    echo "Path no arquivo:"$i
    sed -e 's/-march=\([A-Z0-9a-z]\+\)/-march=native -Ofast/g'  $i > "$i.file_changed"
    mv "$i.file_changed" $i
done



################

sleep 3


#time sudo CONCURRENCY_LEVEL=2 make-kpkg --initrd kernel_image kernel_headers modules_image

time sudo CONCURRENCY_LEVEL=$CL make-kpkg --initrd kernel_image kernel_headers modules_image


cd /usr/src
sudo dpkg -i linux-image-$patchkernel-$ckk\_$patchkernel-$ckk-10.00.Custom_$arqt.deb linux-headers-$patchkernel-$ckk\_$patchkernel-$ckk-10.00.Custom_$arqt.deb

sleep 3

cd /lib/modules
sudo mkinitramfs -o /boot/initrd.img-$patchkernel-$ckk $patchkernel-$ckk
sudo update-grub

sleep 5
echo 'tudo belezinha'


```download is install BFS + BFQ + UBUNTU PATCHS + CFLAGS -march=native -Ofast


version 3.5.2

scriptkernel = kernel linux 3.5.2 + 3.5-ck1 BFS + 3.5.0 BFQ + -Ofast cflag:

```

#!/bin/bash

# script PARA USUARIOS DO UBUNTU 11.10 baixa e compila kernel tudo automaticamente CRIADO PELOS USUÁRIOS DO FORUM UBUNTU BR:
# http://ubuntuforum-br.org/index.php/topic,95318.0.html
#
#
# http://ubuntuforum-br.org/index.php/topic,29799.3960.html
#
#
# Pagina do projeto:
#
# http://sourceforge.net/projects/scriptkernel/
#
# totalmente GPL-3
#
# 
#
# 
# script de compilação do kernel 3.3.X para uso no ubuntu 11.10 64 bits, 
# baixa tudo automaticamente (dependências, compiladores, 
# kernel e patchs) com patch 3.3.0-ck1(BFS) + BFQ   e usando cflag -march=native + -Ofast.
#
# para usa-lo salve ele com o nome de scriptkernel e para executa-lo, utilize um terminal MAXIMIZADO e execute:
#
# $ time sudo bash scriptkernel
#
# e em 2 minutos aparecerá uma tela do menuconfig, 
# escolha a sua arquitetura de seu processador na parte PROCESSOR TYPE AND FEATURES e depois clicke em EXIT e em YES,  
# e logo começará a compilação e no final a instalação automatica.
#
# OBS= para maior exito na compilação (certeza que irá ser executado sem erros) 
# deve ter em seu PC ou NOTEBOOK no mínimo de 2 GB de RAM e ter pelo menos 15 GB livre
# em seu disco rígido (não é uma regra, mas evita de erro por falta de espaço no disco)
#
#
####################################################################################################################################
#
#
# English translation:
#
# Script FOR USERS OF UBUNTU 11.10 low and kernel compiles everything automatically CREATED BY USERS OF THE FORUM BR UBUNTU:
# http://ubuntuforum-br.org/index.php/topic,95318.0.html
#
#
# http://ubuntuforum-br.org/index.php/topic,29799.3960.html
#
#
# http://sourceforge.net/projects/scriptkernel/
#
# Fully GPL-3
#
#
#
#
# Build script for use in kernel 3.X ubuntu 11.10 64 bit
# Low everything automatically (dependencies, compilers,
# Kernel and patches) with patch 3.3.0-ck1(BFS) + BFQ and cflag using -march=native + -Ofast.
#
# Use it to save it with the name of scriptkernel and run it, use a maximized terminal and run:
#
# $ time sudo bash scriptkernel
#
# 2 minutes and a screen of menuconfig,
# Choose the architecture of your processor in the "Processor type and features" and then clicke "EXIT" and "YES",
# And will soon begin to build and end the installation automatically.
#
# OBS = for greater success in the compilation (make sure it will run without errors)
# Must have on your PC or NOTEBOOK at least 2 GB of RAM and at least 15 GB free
# On your hard drive (not a rule but avoids error due to lack of disk space)
#
#
############################################################################################################################################



############################################
#vc só vai ter o trabalho de editar aqui:

#versão do kernel a ser compilado
kernel=3.5

#path de atualização
patchkernel=3.5.2

#patch BFQ
bfq=3.5.0-v4


#patch ck
patchck=3.5-ck1

#sufixo
ckk=ck1


#.config antigo
kernelantigo=atual

############################################

# não precisa mexer em mais nada aqui

##################################
#arquitetura: amd64 ou i386 # criado por Stivekx - forum ubuntu-br #######
arqt=$(dpkg --print-architecture)


#CL=CONCURRENCY_LEVEL do processador # criado por Stivekx  ############
CL=$(grep -c processor /proc/cpuinfo)
##################################

########baixando compiladores e dependencias########################################################
sudo apt-get update
sudo apt-get install kernel-package gcc-4.6 libncurses5 libncurses5-dev build-essential patch gcc make gzip bzip2 lzip lzma lzop lrzip lrzsz  -y
####################################################################################################



######  deletando patchs antigos  #############
sudo rm /usr/src/patch-$patchkernel
sudo rm /usr/src/patch-$patchck
sudo rm /usr/src/0001-base-packaging.patch
sudo rm /usr/src/0002-debian-changelog.patch
sudo rm /usr/src/0003-default-configs.patch
sudo rm /usr/src/0001-block-cgroups-kconfig-build-bits-for-BFQ-v4-$kernel.patch
sudo rm /usr/src/0002-block-introduce-the-BFQ-v4-I-O-sched-for-$kernel.patch
############################################




cd /usr/src
wget -c http://www.kernel.org/pub/linux/kernel/v3.x/linux-$kernel.tar.bz2


sudo tar -jxpvf /usr/src/linux-$kernel.tar.bz2
sudo mv /usr/src/linux-$kernel /usr/src/linux-$patchkernel-$ckk


wget -c http://www.kernel.org/pub/linux/kernel/v3.x/patch-$patchkernel.bz2
wget -c http://ck.kolivas.org/patches/3.0/$kernel/$patchck/patch-$patchck.bz2
wget -c http://algo.ing.unimo.it/people/paolo/disk_sched/patches/$bfq/0001-block-cgroups-kconfig-build-bits-for-BFQ-v4-$kernel.patch
wget -c http://algo.ing.unimo.it/people/paolo/disk_sched/patches/$bfq/0002-block-introduce-the-BFQ-v4-I-O-sched-for-$kernel.patch



#ubuntu patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-quantal/0001-base-packaging.patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-quantal/0002-debian-changelog.patch
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v$patchkernel-quantal/0003-default-configs.patch



sudo bunzip2 /usr/src/patch-$patchkernel.bz2
sudo bunzip2 /usr/src/patch-$patchck.bz2


cd /usr/src/linux-$patchkernel-$ckk

sudo patch -p1 < /usr/src/patch-$patchkernel
sudo patch -p1 < /usr/src/patch-$patchck
sudo patch -p1 < /usr/src/0001-block-cgroups-kconfig-build-bits-for-BFQ-v4-$kernel.patch
sudo patch -p1 < /usr/src/0002-block-introduce-the-BFQ-v4-I-O-sched-for-$kernel.patch
sudo patch -p1 < /usr/src/0001-base-packaging.patch
sudo patch -p1 < /usr/src/0002-debian-changelog.patch
sudo patch -p1 < /usr/src/0003-default-configs.patch


######################
#sudo cp /boot/config-$kernelantigo /usr/src/linux-$patchkernel-$ckk/.config

#### criado por Stivekx #############
config_file=$(locate /boot/config-* | sort -r | head -1)

sudo cp $config_file /usr/src/linux-$patchkernel-$ckk

#########################

#sudo gedit Makefile  

sleep 3

sudo make menuconfig




######## Retirando Modulos Problematicos  ############

sudo sed 's/CONFIG_RTS5139=m/# CONFIG_RTS5139 is not set/g' /usr/src/linux-$patchkernel-$ckk/.config > /usr/src/linux-$patchkernel-$ckk/aa && mv /usr/src/linux-$patchkernel-$ckk/aa /usr/src/linux-$patchkernel-$ckk/.config

sleep 2

#sudo sed 's/CONFIG_NO_HZ=y/# CONFIG_NO_HZ is not set/g' /usr/src/linux-$patchkernel-$ckk/.config > /usr/src/linux-$patchkernel-$ckk/bb && mv /usr/src/linux-$patchkernel-$ckk/bb /usr/src/linux-$patchkernel-$ckk/.config

#sleep3

######################################################


############ script criado por Stivekx #######################

#!/bin/bash

#Script para automatizar a mudança das flags na hora de compilar o kernel.
#Mais informações sobre como compilar o kernel para seu processador:
#http://ubuntuforum-br.org/index.php/topic,81718.0.html

#Modo de usar:
#Após baixar o kernel, descompactar, criar um link simbólico para ele no /usr/src/linux:
# cd /usr/src/linux    
# sudo su
# chmod +x script.sh
# ./script.sh
#O script deve ser executado como root. Recomendo que use sudo su - e rode o script ao invés de sudo sh script.sh


#Script criado por André Steinn

#Aqui é a lista de arquivos que ele vai dar replace no -march= por -march=native. Você pode mudar essa lista de arquivos passando a lista pela opção a e separados pro virgula
#e.g.: ./script.sh -a arch/x86/boot/compressed/Makefile,arch/x86/boot/Makefile,arquivo1,arquivo2,arquivo3

arquivos=( "arch/x86/boot/compressed/Makefile" "arch/x86/boot/Makefile" "arch/x86/kernel/acpi/realmode/Makefile" "arch/x86/Kconfig.cpu" "arch/x86/Makefile" "arch/x86/Makefile_32.cpu")

#Aqui eu verifico se a pessoa passou algum argumento na hora de executar o script
while getopts ":a:c" opt; do
  case $opt in
    a)
      echo "Você setou uma lista de arquivos personalizada: $OPTARG" >&2
    IFS=',' read -ra arquivos <<< "$OPTARG"
      ;;
    \?)
      echo "Opção inválida: -$OPTARG" >&2
      exit 1
      ;;
  esac
done

#Aqui eu faço um loop e altero os arquivos, removendo o -march=() por -march=native
for i in "${arquivos[@]}"
do
    echo "Path no arquivo:"$i
    sed -e 's/-march=\([A-Z0-9a-z]\+\)/-march=native -Ofast/g'  $i > "$i.file_changed"
    mv "$i.file_changed" $i
done



################

sleep 3


#time sudo CONCURRENCY_LEVEL=2 make-kpkg --initrd kernel_image kernel_headers modules_image

time sudo CONCURRENCY_LEVEL=$CL make-kpkg --initrd kernel_image kernel_headers modules_image


cd /usr/src
sudo dpkg -i linux-image-$patchkernel-$ckk\_$patchkernel-$ckk-10.00.Custom_$arqt.deb linux-headers-$patchkernel-$ckk\_$patchkernel-$ckk-10.00.Custom_$arqt.deb

sleep 3

cd /lib/modules
sudo mkinitramfs -o /boot/initrd.img-$patchkernel-$ckk $patchkernel-$ckk
sudo update-grub

sleep 5
echo 'tudo belezinha'

```


[http://sourceforge.net/projects/scriptkernel/files/](http://sourceforge.net/projects/scriptkernel/files/)


...; )

---

