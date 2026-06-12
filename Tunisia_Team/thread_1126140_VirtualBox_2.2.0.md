---
title: "VirtualBox 2.2.0"
date: 2009-04-15
forum: Tunisia Team
---

### Post by MaWaLe on 2009-04-15
Bonjour tout le monde

depuis maintenant deux jours, la nouvelle version stable de VirtuakBox vient d'être publiée officiellement : à savoir la version 2.2.0

Parmis les nouveautés de cette versions :
- Une meilleure intégration avec la nouvelle version d'Ubuntu (pour montrer que le monde se tourne de plus en plus vers NOTRE OS) : il y avait un petit problème pour l'affichage en plein écran d'une VM Jaunty et ce parce que la nouvelle version su serveur xorg (1.6.0) installée par défaut avec Jaunty n'est pas prise en charge par vBox.
- Une prise en charge complète des supports USB : Avant il y avait certaines acrobaties à effectuer pour récupérer son Flash ou son imprimante sous la VM. Maintenant il suffit d'installer vBox et le tour est joué :) Cette nouveauté est bonne pour les gens qui sauront gérer la situation avec l'accès direct aux Flash sous Windows donc possibilité de passage directe de virus via la Flash mais pour les novices, ça sera une source de danger.


enfin la liste des nouveautés est longue mais personnellement je n'ai reportée que ces deux là qui peuvent intéresser la majorité des utilisateurs profanes (pour l'USB) et un peu plus avancés (installation des stations de test Jaunty sous vBox).

Bonne journée.

PS : si vous faites une installation manuelle, il ne faut pas oublier qu'il faut désinstaller manuellement aussi la version précédente déjà installée sinon si vous faite l'installation à partir de synaptic (donc dépôt propre de vBox ajouté à votre** source.list** alors la désinstallation de l'ancienne version et l'installation de la nouvelle se fait automatiquement)

---

### Post by RachedTN on 2009-04-16
Juste une petite rectification, VirtualBox 2.2.0 vient de sortir il y'a une semaine maintenant :
New Apr 8, 2009
VirtualBox 2.2.0 released!
Sun today released VirtualBox 2.2.0 which marks another major milestone for the world's most popular free and open source hypervisor. Among the many improvements are support for OVF appliances, 3D acceleration for Linux/Solaris guests and support for up to 16GB of RAM per virtual machine. See the ChangeLog for a list of changes since VirtualBox 2.1. 

Voici les nouveautés (en anglais)

    * OVF (Open Virtualization Format) appliance import and export (see chapter 3.8, Importing and exporting virtual machines, User Manual page 55)
    * Host-only networking mode (see chapter 6.7, Host-only networking, User Manual page 88)
    * Hypervisor optimizations with signi&#64257;cant performance gains for high context switching rates
    * Raised the memory limit for VMs on 64-bit hosts to 16GB
    * VT-x/AMD-V are enabled by default for newly created virtual machines
    * USB (OHCI & EHCI) is enabled by default for newly created virtual machines (Qt GUI only)
    * Experimental USB support for OpenSolaris hosts
    * Shared folders for Solaris and OpenSolaris guests
    * OpenGL 3D acceleration for Linux and Solaris guests (see chapter 4.8, Hardware 3D acceleration (OpenGL), User Manual page 70)
    * Added C API in addition to C++, Java, Python and Web Services 

Source : [www.virtualbox.com](www.virtualbox.com)

---

