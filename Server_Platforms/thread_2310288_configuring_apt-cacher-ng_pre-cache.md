---
title: "configuring apt-cacher-ng pre-cache"
date: 2016-01-18
forum: Server Platforms
---

### Post by Spency on 2016-01-18
I use to run an apt-mirror server which is now a soon to be apt-cacher-ng server. I was wondering how to use my existing apt-mirror info to configure my apt-cacher-ng pre-cache mirror.

Apt-mirror config:
```
############# config ################### 
set base_path    /opt/apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
set limit_rate 10k
#
############# end config ##############
# Day
############# TRUSTY ################


deb-i386 http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu trusty-proposed main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse


deb-amd64 http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
#deb-amd64 http://archive.ubuntu.com/ubuntu trusty-proposed main restricted universe multiverse
#deb-amd64 http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse


deb-src http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu trusty-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse


########### VIVID ###################


deb-i386 http://archive.ubuntu.com/ubuntu vivid main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu vivid-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu vivid-updates main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu vivid-proposed main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu vivid-backports main restricted universe multiverse


deb-amd64 http://archive.ubuntu.com/ubuntu vivid main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu vivid-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu vivid-updates main restricted universe multiverse
#deb-amd64 http://archive.ubuntu.com/ubuntu vivid-proposed main restricted universe multiverse
#deb-amd64 http://archive.ubuntu.com/ubuntu vivid-backports main restricted universe multiverse


deb-src http://archive.ubuntu.com/ubuntu vivid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu vivid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu vivid-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu vivid-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu vivid-backports main restricted universe multiverse


############ WILY ###############


deb-i386 http://archive.ubuntu.com/ubuntu wily main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu wily-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu wily-updates main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu wily-proposed main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse

deb-amd64 http://archive.ubuntu.com/ubuntu wily main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu wily-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu wily-updates main restricted universe multiverse
#deb-amd64 http://archive.ubuntu.com/ubuntu wily-proposed main restricted universe multiverse
#deb-amd64 http://archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse


deb-src http://archive.ubuntu.com/ubuntu wily main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu wily-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu wily-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu wily-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse


########### OIBAF ###########
# deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main


# deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu vivid main
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu vivid main


# deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu wily main
# deb-src http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu wily main


######### SARNEX ###########
# deb http://ppa.launchpad.net/commendsarnex/winedri3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/commendsarnex/winedri3/ubuntu trusty main


# deb http://ppa.launchpad.net/commendsarnex/winedri3/ubuntu vivid main
# deb-src http://ppa.launchpad.net/commendsarnex/winedri3/ubuntu vivid main


# deb http://ppa.launchpad.net/commendsarnex/winedri3/ubuntu wily main
# deb-src http://ppa.launchpad.net/commendsarnex/winedri3/ubuntu wily main


######## IXIT MASTER ########
# deb http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu trusty main
# deb-src http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu trusty main

# deb http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu vivid main
# deb-src http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu vivid main


# deb http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu wily main
# deb-src http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu wily main


####### SPOTIFY ########
# deb http://repository.spotify.com stable non-free


clean http://archive.ubuntu.com/ubuntu


```

Apt-cacher-ng pre-cache config
```


# Precache a set of files referenced by specified index files. This can be used
# to create a partial mirror usable for offline work. There are certain limits
# and restrictions on the path specification, see manual and the cache control
# web site for details. A list of (maybe) relevant index files could be
# retrieved via "apt-get --print-uris update" on a client machine.
# 
# Example:
# PrecacheFor: debrep/dists/unstable/*/source/Sources* debrep/dists/unstable/*/binary-amd64/Packages*

```

In the example debrep is a remap of deb_mirror.gz
```

# Repository remapping. See manual for details.
# In this example, some backends files might be generated during package
# installation using information collected on the system.
# Examples:
Remap-debrep: file:deb_mirror*.gz /debian ; file:backends_debian # Debian Archives
Remap-uburep: file:ubuntu_mirrors /ubuntu ; file:backends_ubuntu # Ubuntu Archives
Remap-debvol: file:debvol_mirror*.gz /debian-volatile ; file:backends_debvol # Debian Volatile Archives
Remap-cygwin: file:cygwin_mirrors /cygwin # ; file:backends_cygwin # incomplete, please create this file or specify $
Remap-sfnet:  file:sfnet_mirrors # ; file:backends_sfnet # incomplete, please create this file or specify preferred $
Remap-alxrep: file:archlx_mirrors /archlinux # ; file:backend_archlx # Arch Linux
Remap-fedora: file:fedora_mirrors # Fedora Linux
Remap-epel:   file:epel_mirrors # Fedora EPEL
Remap-slrep:  file:sl_mirrors # Scientific Linux
#Remap-gentoo: file:gentoo_mirrors.gz /gentoo ; file:backends_gentoo # Gentoo Archives
```

When unpacked deb_mirror.gz produces dev_mirror which reads:
```



http://artfiles.org/debian/
http://be.mirror.eurid.eu/debian/
http://buaya.klas.or.id/debian/
http://carroll.aset.psu.edu/pub/linux/distributions/debian/
http://cdn.debian.net/debian/
http://deb-mir1.naitways.net/debian/
http://deb-mirror.de/debian/
http://deb.vanvps.com/debian/
http://debian.advalem.net/debian/
http://debian.asis.io/debian/
http://debian.balt.net/debian/
http://debian.bhs.mirrors.ovh.net/debian/
http://debian.bjtu.edu.cn/debian/
http://debian.bononia.it/debian/
http://debian.bsnet.se/debian/
http://debian.c3sl.ufpr.br/debian/
http://debian.cabletel.com.mk/debian/
http://debian.carnet.hr/debian/
http://debian.cc.lehigh.edu/debian/
http://debian.cites.illinois.edu/pub/debian/
http://debian.co.il/debian/
http://debian.corenetworks.net/debian/
http://debian.cs.binghamton.edu/debian/
http://debian.csail.mit.edu/debian/
http://debian.cse.msu.edu/debian/
http://debian.csg.uzh.ch/debian/
http://debian.csie.nctu.edu.tw/debian/
http://debian.csie.ntu.edu.tw/debian/
http://debian.dcc.fc.up.pt/debian/
http://debian.doratelekom.com/debian/
http://debian.dynamica.it/debian/
http://debian.ec.as6453.net/debian/
http://debian.ens-cachan.fr/ftp/debian/
http://debian.ethz.ch/debian/
http://debian.fastbull.org/debian/
http://debian.fastweb.it/debian/
http://debian.gnu.gen.tr/debian/
http://debian.grena.ge/debian/
http://debian.grn.cat/debian/
http://debian.gtisc.gatech.edu/debian/
http://debian.heanet.ie/debian/
http://debian.ignum.cz/debian/
http://debian.inhost.pro/debian/
http://debian.inode.at/debian/
http://debian.insacom.cl/debian/
http://debian.intergenia.de/debian/
http://debian.ipacct.com/debian/
http://debian.iskon.hr/debian/
http://debian.koyanet.lv/debian/
http://debian.lagis.at/debian/
http://debian.lagoon.nc/debian/
http://debian.las.ic.unicamp.br/debian/
http://debian.linux.edu.lv/debian/
http://debian.lth.se/debian/
http://debian.ludost.net/debian/
http://debian.man.ac.uk/debian/
http://debian.med.univ-tours.fr/debian/
http://debian.mirror.ac.ke/debian/
http://debian.mirror.cambrium.nl/debian/
http://debian.mirror.constant.com/debian/
http://debian.mirror.dkm.cz/debian/
http://debian.mirror.frontiernet.net/debian/
http://debian.mirror.gtcomm.net/debian/
http://debian.mirror.iphh.net/debian/
http://debian.mirror.iweb.ca/debian/
http://debian.mirror.lrz.de/debian/
http://debian.mirror.neology.co.za/debian/
http://debian.mirror.netelligent.ca/debian/
http://debian.mirror.rafal.ca/debian/
http://debian.mirror.root.lu/debian/
http://debian.mirror.tn/debian/
http://debian.mirror.uber.com.au/debian/
http://debian.mirror.uk.sargasso.net/debian/
http://debian.mirror.vu.lt/debian/
http://debian.mirror.web4u.cz/
http://debian.mirrors.crysys.hu/debian/
http://debian.mirrors.easynet.fr/debian/
http://debian.mirrors.ovh.net/debian/
http://debian.mirrors.tds.net/debian/
http://debian.mnet.bg/debian/
http://debian.morphium.info/debian/
http://debian.mur.at/debian/
http://debian.nautile.nc/debian/
http://debian.nctu.edu.tw/debian/
http://debian.netcologne.de/debian/
http://debian.netlinux.cl/debian/
http://debian.netvisao.pt/
http://debian.nsu.ru/debian/
http://debian.opensourcemirror.com/debian/
http://debian.org.ua/debian/
http://debian.osdn.org.ua/debian/
http://debian.osuosl.org/debian/
http://debian.otenet.gr/debian/
http://debian.polytech-lille.fr/debian/
http://debian.pop-sc.rnp.br/debian/
http://debian.proxad.net/debian/
http://debian.revolsys.fr/debian/
http://debian.salud.gob.sv/debian/
http://debian.savoirfairelinux.net/debian/
http://debian.securedservers.com/debian/


http://debian.serverspace.co.uk/debian/
http://debian.sil.at/debian/
http://debian.simnet.is/debian/
http://debian.skarta.net/debian/
http://debian.spnet.net/debian/
http://debian.sth.sze.hu/debian/
http://debian.stream.uz/debian/
http://debian.superhosting.cz/debian/
http://debian.telecoms.bg/debian/
http://debian.telsatbb.vu/debian/
http://debian.tu-bs.de/debian/
http://debian.uchicago.edu/debian/
http://debian.ues.edu.sv/debian/
http://debian.unal.edu.co/debian/
http://debian.uni-duisburg-essen.de/debian/
http://debian.uni.edu.ni/debian/
http://debian.uniminuto.edu/debian/
http://debian.univ-lorraine.fr/debian/
http://debian.univ-reims.fr/debian/
http://debian.univ-tlse2.fr/debian/
http://debian.ustc.edu.cn/debian/
http://debian.usu.edu/debian/
http://debian.volia.net/debian/
http://debian.yorku.ca/debian/
http://debianmirror.nkn.in/debian/
http://debmirror.amis.net/debian/
http://debs.pelotas.ifsul.edu.br/debian/
http://dennou-h.gfd-dennou.org/debian/
http://dennou-k.gfd-dennou.org/debian/
http://dennou-q.gfd-dennou.org/debian/
http://download.unesp.br/linux/debian/
http://free.hands.com/debian/
http://freedom.dicea.unifi.it/ftp/pub/linux/debian/
http://ftp-chi.osuosl.org/debian/
http://ftp-mirror.internap.com/pub/debian/
http://ftp-nyc.osuosl.org/debian/
http://ftp-stud.hs-esslingen.de/debian/
http://ftp.acc.umu.se/debian/
http://ftp.antik.sk/debian/
http://ftp.arnes.si/pub/packages/debian/
http://ftp.aso.ee/debian/
http://ftp.at.debian.org/debian/
http://ftp.au.debian.org/debian/
http://ftp.availo.se/debian/
http://ftp.ba.debian.org/debian/
http://ftp.be.debian.org/debian/
http://ftp.belnet.be/debian/
http://ftp.bg.debian.org/debian/
http://ftp.bme.hu/debian/
http://ftp.br.debian.org/debian/
http://ftp.by.debian.org/debian/
http://ftp.ca.debian.org/debian/
http://ftp.caliu.cat/debian/
http://ftp.carnet.hr/debian/
http://ftp.cc.uoc.gr/mirrors/linux/debian/
http://ftp.ccc.uba.ar/pub/linux/debian/debian/
http://ftp.ch.debian.org/debian/
http://ftp.cica.es/debian/
http://ftp.citylink.co.nz/debian/
http://ftp.cl.debian.org/debian/
http://ftp.cn.debian.org/debian/
http://ftp.corbina.net/debian/
http://ftp.crihan.fr/debian/
http://ftp.cvut.cz/debian/
http://ftp.cz.debian.org/debian/
http://ftp.daum.net/debian/
http://ftp.de.debian.org/debian/
http://ftp.debian.chuvsu.ru/debian/
http://ftp.debian.com/debian/
http://ftp.debian.nl/debian/
http://ftp.debian.org.hk/debian/
http://ftp.debian.org/debian/
http://ftp.debian.sk/debian/
http://ftp.debian.skynet.be/ftp/debian/
http://ftp.debianclub.org/debian/
http://ftp.dk.debian.org/debian/
http://ftp.ds.karen.hj.se/debian/
http://ftp.ec-m.fr/debian/
http://ftp.ee.debian.org/debian/
http://ftp.eq.uc.pt/software/Linux/debian/
http://ftp.es.debian.org/debian/
http://ftp.fi.debian.org/debian/
http://ftp.fr.debian.org/debian/
http://ftp.freenet.de/debian/
http://ftp.fsn.hu/debian/
http://ftp.funet.fi/pub/linux/mirrors/debian/
http://ftp.gr.debian.org/debian/
http://ftp.gtlib.gatech.edu/debian/
http://ftp.gul.uc3m.es/debian/
http://ftp.gva.es/mirror/debian/
http://ftp.halifax.rwth-aachen.de/debian/
http://ftp.hk.debian.org/debian/
http://ftp.hosteurope.de/mirror/ftp.debian.org/debian/
http://ftp.hr.debian.org/debian/
http://ftp.hu.debian.org/debian/
http://ftp.icm.edu.pl/pub/Linux/debian/
http://ftp.ie.debian.org/debian/
http://ftp.iinet.net.au/debian/debian/
http://ftp.iitm.ac.in/debian/
http://ftp.informatik.rwth-aachen.de/ftp/pub/Linux/debian/
http://ftp.informatik.uni-frankfurt.de/debian/
http://ftp.irb.hr/debian/
http://ftp.is.debian.org/debian/
http://ftp.it.debian.org/debian/
http://ftp.iut-bm.univ-fcomte.fr/debian/
http://ftp.jaist.ac.jp/debian/
http://ftp.jp.debian.org/debian/
http://ftp.kfki.hu/linux/debian/
http://ftp.kr.debian.org/debian/
http://ftp.lecl.net/debian/
http://ftp.linux.org.tr/debian/
http://ftp.lip6.fr/pub/linux/distributions/debian/
http://ftp.litnet.lt/debian/
http://ftp.lt.debian.org/debian/
http://ftp.lug.ro/debian/
http://ftp.man.poznan.pl/pub/linux/debian/debian/
http://ftp.metu.edu.tr/debian/
http://ftp.monash.edu.au/pub/linux/debian/
http://ftp.mx.debian.org/debian/
http://ftp.nc.debian.org/debian/
http://ftp.neowiz.com/debian/
http://ftp.nerim.net/debian/http://ftp.nl.debian.org/debian/
http://ftp.nluug.nl/pub/os/Linux/distr/debian/
http://ftp.no.debian.org/debian/
http://ftp.nz.debian.org/debian/
http://ftp.pl.debian.org/debian/
http://ftp.plusline.de/debian/
http://ftp.proxad.net/mirrors/ftp.debian.org/
http://ftp.psn.ru/debian/
http://ftp.pt.debian.org/debian/
http://ftp.pwr.wroc.pl/debian/
http://ftp.rediris.es/debian/
http://ftp.rezopole.net/debian/
http://ftp.rhnet.is/debian/
http://ftp.riken.jp/Linux/debian/debian/
http://ftp.ro.debian.org/debian/
http://ftp.roedu.net/debian/
http://ftp.ru.debian.org/debian/
http://ftp.se.debian.org/debian/
http://ftp.seclan.com/debian/
http://ftp.si.debian.org/debian/
http://ftp.sk.debian.org/debian/
http://ftp.stw-bonn.de/debian/
http://ftp.sunet.se/pub/Linux/distributions/debian/
http://ftp.surfnet.nl/os/Linux/distr/debian/
http://ftp.sv.debian.org/debian/
http://ftp.task.gda.pl/debian/
http://ftp.th.debian.org/debian/
http://ftp.ticklers.org/debian/
http://ftp.tiscali.nl/debian/
http://ftp.tku.edu.tw/debian/
http://ftp.tr.debian.org/debian/
http://ftp.tsukuba.wide.ad.jp/debian/
http://ftp.tu-chemnitz.de/pub/linux/debian/debian/
http://ftp.tu-clausthal.de/pub/linux/debian/
http://ftp.tu-graz.ac.at/mirror/debian/
http://ftp.tw.debian.org/debian/
http://ftp.u-picardie.fr/mirror/debian/
http://ftp.u-strasbg.fr/debian/
http://ftp.ua.debian.org/debian/
http://ftp.udc.es/debian/
http://ftp.uk.debian.org/debian/
http://ftp.uni-bayreuth.de/debian/
http://ftp.uni-erlangen.de/debian/
http://ftp.uni-kl.de/debian/
http://ftp.uni-koeln.de/debian/
http://ftp.uni-sofia.bg/debian/
http://ftp.univ-pau.fr/linux/mirrors/debian/
http://ftp.univie.ac.at/systems/linux/debian/debian/
http://ftp.us.debian.org/debian/
http://ftp.utexas.edu/debian/
http://ftp.vectranet.pl/debian/
http://ftp.zcu.cz/mirrors/debian/
http://ftp2.de.debian.org/debian/
http://ftp2.debian.org.ua/debian/
http://ftp2.fr.debian.org/debian/
http://ftp3.nrc.ca/debian/http://ftp5.gwdg.de/pub/linux/debian/debian/
http://gd.tuwien.ac.at/opsys/linux/debian/
http://giano.com.dist.unige.it/debian/
http://glua.ua.pt/mirrors/distro/debian/archive/
http://http.debian.net/debian/
http://kambing.ui.ac.id/debian/
http://kartolo.sby.datautama.net.id/debian/
http://kebo.vlsm.org/debian/
http://linorg.usp.br/debian/
http://lug.mtu.edu/debian/
http://merlin.fit.vutbr.cz/debian/
http://mi.mirror.garr.it/mirrors/debian/
http://mirror.0x.sg/debian/
http://mirror.1000mbps.com/debian/
http://mirror.1und1.de/debian/
http://mirror.ancl.hawaii.edu/linux/debian/
http://mirror.anl.gov/debian/
http://mirror.as24220.net/pub/debian/
http://mirror.as35701.net/debian/
http://mirror.as43289.net/debian/
http://mirror.bytemark.co.uk/debian/
http://mirror.cc.columbia.edu/debian/
http://mirror.cogentco.com/debian/
http://mirror.cpsc.ucalgary.ca/mirror/debian.org/debian/
http://mirror.crucial.com.au/debian/
http://mirror.csclub.uwaterloo.ca/debian/
http://mirror.cse.iitk.ac.in/debian/
http://mirror.cse.unsw.edu.au/debian/http://mirror.datacenter.by/debian/
http://mirror.de.leaseweb.net/debian/
http://mirror.debian.com.ba/debian/
http://mirror.debian.ikoula.com/debian/
http://mirror.debian.vn/debian/
http://mirror.easyspeedy.com/debian/
http://mirror.eftel.com/debian/
http://mirror.fdcservers.net/debian/
http://mirror.hmc.edu/debian/
http://mirror.i3d.net/pub/debian/
http://mirror.isoc.org.il/pub/debian/
http://mirror.it.ubc.ca/debian/
http://mirror.its.dal.ca/debian/
http://mirror.kku.ac.th/debian/
http://mirror.linux.org.au/debian/
http://mirror.mephi.ru/debian/
http://mirror.mirohost.net/debian/
http://mirror.mythic-beasts.com/debian/
http://mirror.neolabs.kz/debian/
http://mirror.network.kz/debian/
http://mirror.nexcess.net/debian/
http://mirror.nl.leaseweb.net/debian/
http://mirror.nus.edu.sg/Debian/
http://mirror.optus.net/debian/
http://mirror.overthewire.com.au/debian/
http://mirror.ox.ac.uk/debian/
http://mirror.peer1.net/debian/
http://mirror.picosecond.org/debian/http://mirror.pmf.kg.ac.rs/debian/
http://mirror.positive-internet.com/debian/
http://mirror.pregi.net/debian/
http://mirror.proserve.nl/debian/
http://mirror.rit.edu/debian/
http://mirror.sov.uk.goscomb.net/debian/
http://mirror.steadfast.net/debian/
http://mirror.switch.ch/ftp/mirror/debian/
http://mirror.thelinuxfix.com/debian/
http://mirror.unej.ac.id/debian/
http://mirror.unitedcolo.de/debian/
http://mirror.units.it/debian/
http://mirror.us.leaseweb.net/debian/
http://mirror.vorboss.net/debian/
http://mirror.waia.asn.au/debian/
http://mirror.yandex.ru/debian/
http://mirror.zol.co.zw/debian/
http://mirror2.corbina.ru/debian/
http://mirrors.163.com/debian/
http://mirrors.accretive-networks.net/debian/
http://mirrors.acm.jhu.edu/debian/
http://mirrors.advancedhosters.com/debian/
http://mirrors.bloomu.edu/debian/
http://mirrors.compuscene.org/debian/
http://mirrors.dcarsat.com.ar/debian/
http://mirrors.dotsrc.org/debian/
http://mirrors.eastera.tj/debian/
http://mirrors.fe.up.pt/debian/
http://mirrors.gigenet.com/debian/
http://mirrors.ircam.fr/pub/debian/
http://mirrors.ispros.com.bd/debian/
http://mirrors.kernel.org/debian/
http://mirrors.linux.iu.edu/linux/debian/
http://mirrors.melbourne.co.uk/debian/
http://mirrors.modwest.com/debian/
http://mirrors.nfsi.pt/debian/
http://mirrors.rackhosting.com/debian/
http://mirrors.serverhost.ro/debian/
http://mirrors.sohu.com/debian/
http://mirrors.syringanetworks.net/debian/
http://mirrors.tecnoera.com/debian/
http://mirrors.telianet.dk/debian/
http://mirrors.tummy.com/debian/
http://mirrors.tuna.tsinghua.edu.cn/debian/
http://mirrors.ucr.ac.cr/debian/
http://mirrors.xenir.com/debian/
http://mirrors.xmission.com/debian/
http://mirrorservice.org/sites/ftp.debian.org/debian/
http://mmc.geofisica.unam.mx/debian/
http://nl.mirror.eurid.eu/debian/
http://noodle.portalus.net/debian/
http://opensource.nchc.org.tw/debian/
http://repository.linux.pf/debian/
http://sft.if.usp.br/debian/
http://shadow.ind.ntou.edu.tw/debian/
http://suro.ubaya.ac.id/debian/
http://the.earth.li/debian/
http://ukdebian.mirror.anlx.net/debian/
http://ulises.hostalia.com/debian/
http://webb.ens-cachan.fr/debian/
http://www.anheng.com.cn/debian/
```

Now in the remapping section uburep is remapped to the already unpacked ubuntu_mirrors file:
```

http://76.73.4.58/ubuntu/
http://ac.archive.ubuntu.com/ubuntu/
http://ad.archive.ubuntu.com/ubuntu/
http://ae.archive.ubuntu.com/ubuntu/
http://af.archive.ubuntu.com/ubuntu/
http://ag.archive.ubuntu.com/ubuntu/
http://ai.archive.ubuntu.com/ubuntu/
http://al.archive.ubuntu.com/ubuntu/
http://am.archive.ubuntu.com/ubuntu/
http://an.archive.ubuntu.com/ubuntu/
http://ao.archive.ubuntu.com/ubuntu/
http://aq.archive.ubuntu.com/ubuntu/
http://ar.archive.ubuntu.com/ubuntu/
http://archive.linux.duke.edu/ubuntu/
http://archive.mirror.blix.com/ubuntu/
http://archive.ubuntu.com.ba/ubuntu/
http://archive.ubuntu.com/ubuntu/
http://archive.ubuntu.csg.uzh.ch/ubuntu/
http://archive.ubuntu.mirror.dkm.cz/
http://archive.ubuntu.nautile.nc/ubuntu/
http://archive.ubuntu.sin1.openmirrors.asia/ubuntu/
http://archive.ubuntu.totaal.net/
http://archive.ubuntu.webxcreen.org/
http://archive.ubuntumirror.dei.uc.pt/ubuntu/
http://artfiles.org/ubuntu.com/
http://as.archive.ubuntu.com/ubuntu/
http://at.archive.ubuntu.com/ubuntu/
http://au.archive.ubuntu.com/ubuntu/
http://aw.archive.ubuntu.com/ubuntu/
http://ax.archive.ubuntu.com/ubuntu/
http://az.archive.ubuntu.com/ubuntu/
http://ba.archive.ubuntu.com/ubuntu/
http://bb.archive.ubuntu.com/ubuntu/
http://bd.archive.ubuntu.com/ubuntu/
http://be.archive.ubuntu.com/ubuntu/
http://bf.archive.ubuntu.com/ubuntu/
http://bg.archive.ubuntu.com/ubuntu/
http://bh.archive.ubuntu.com/ubuntu/
http://bi.archive.ubuntu.com/ubuntu/
http://bj.archive.ubuntu.com/ubuntu/
http://bl.archive.ubuntu.com/ubuntu/
http://bm.archive.ubuntu.com/ubuntu/
http://bn.archive.ubuntu.com/ubuntu/
http://bo.archive.ubuntu.com/ubuntu/
http://bouyguestelecom.ubuntu.lafibre.info/ubuntu/
http://bq.archive.ubuntu.com/ubuntu/
http://br.archive.ubuntu.com/ubuntu/
http://bs.archive.ubuntu.com/ubuntu/
http://bt.archive.ubuntu.com/ubuntu/
http://buaya.klas.or.id/ubuntu/
http://bv.archive.ubuntu.com/ubuntu/
http://bw.archive.ubuntu.com/ubuntu/
http://by.archive.ubuntu.com/ubuntu/
http://bz.archive.ubuntu.com/ubuntu/
http://ca.archive.ubuntu.com/ubuntu/
http://cc.archive.ubuntu.com/ubuntu/
http://cd.archive.ubuntu.com/ubuntu/
http://cesium.di.uminho.pt/pub/ubuntu-archive/
http://cf.archive.ubuntu.com/ubuntu/
http://cg.archive.ubuntu.com/ubuntu/
http://ch.archive.ubuntu.com/ubuntu/
http://ci.archive.ubuntu.com/ubuntu/
http://ck.archive.ubuntu.com/ubuntu/
http://cl.archive.ubuntu.com/ubuntu/
http://cm.archive.ubuntu.com/ubuntu/
http://cn.archive.ubuntu.com/ubuntu/
http://co.archive.ubuntu.com/ubuntu/
http://cosmos.cites.illinois.edu/pub/ubuntu/
http://cr.archive.ubuntu.com/ubuntu/
http://cu.archive.ubuntu.com/ubuntu/
http://cv.archive.ubuntu.com/ubuntu/
http://cw.archive.ubuntu.com/ubuntu/
http://cx.archive.ubuntu.com/ubuntu/
http://cy.archive.ubuntu.com/ubuntu/
http://cz.archive.ubuntu.com/ubuntu/
http://de.archive.ubuntu.com/ubuntu/
http://de2.archive.ubuntu.com/ubuntu/
http://debian.charite.de/ubuntu/
http://distrib-coffee.ipsl.jussieu.fr/pub/linux/ubuntu/
http://distrib-coffee.ipsl.jussieu.fr/ubuntu/
http://dj.archive.ubuntu.com/ubuntu/
http://dk.archive.ubuntu.com/ubuntu/
http://dl2.foss-id.web.id/ubuntu/
http://dm.archive.ubuntu.com/ubuntu/
http://do.archive.ubuntu.com/ubuntu/
http://download.nus.edu.sg/mirror/ubuntu/
http://dz.archive.ubuntu.com/ubuntu/
http://ec.archive.ubuntu.com/ubuntu/
http://ee.archive.ubuntu.com/ubuntu/
http://eg.archive.ubuntu.com/ubuntu/
http://eh.archive.ubuntu.com/ubuntu/
http://er.archive.ubuntu.com/ubuntu/
http://es.archive.ubuntu.com/ubuntu/
http://espelhos.edugraf.ufsc.br/ubuntu/
http://et.archive.ubuntu.com/ubuntu/
http://eu.archive.ubuntu.com/ubuntu/
http://fi.archive.ubuntu.com/ubuntu/
http://fj.archive.ubuntu.com/ubuntu/
http://fk.archive.ubuntu.com/ubuntu/
http://fm.archive.ubuntu.com/ubuntu/
http://fo.archive.ubuntu.com/ubuntu/
http://fr.archive.ubuntu.com/ubuntu/
http://free.nchc.org.tw/ubuntu/
http://ftp-stud.hs-esslingen.de/ubuntu/
http://ftp.acc.umu.se/ubuntu/
http://ftp.antik.sk/ubuntu/
http://ftp.arnes.si/pub/mirrors/ubuntu/
http://ftp.astral.ro/mirrors/ubuntu.com/ubuntu/
http://ftp.availo.se/ubuntu/
http://ftp.belnet.be/ubuntu.com/ubuntu/
http://ftp.byfly.by/ubuntu/
http://ftp.caliu.cat/pub/distribucions/ubuntu/archive/
http://ftp.cc.uoc.gr/mirrors/linux/ubuntu/packages/
http://ftp.ccc.uba.ar/pub/linux/ubuntu/
http://ftp.citylink.co.nz/ubuntu/
http://ftp.crihan.fr/ubuntu/
http://ftp.cuhk.edu.hk/pub/Linux/ubuntu/
http://ftp.cvut.cz/ubuntu/
http://ftp.dat.etsit.upm.es/ubuntu/
http://ftp.daum.net/ubuntu/
http://ftp.ds.karen.hj.se/ubuntu/
http://ftp.estpak.ee/ubuntu/
http://ftp.fau.de/ubuntu/
http://ftp.gts.lug.ro/ubuntu/
http://ftp.halifax.rwth-aachen.de/ubuntu/
http://ftp.hawo.stw.uni-erlangen.de/ubuntu/
http://ftp.heanet.ie/pub/ubuntu/
http://ftp.hosteurope.de/mirror/archive.ubuntu.com/
http://ftp.icm.edu.pl/pub/Linux/ubuntu/
http://ftp.iinet.net.au/pub/ubuntu/
http://ftp.iitm.ac.in/ubuntu/
http://ftp.info.uvt.ro/ubuntu/
http://ftp.jaist.ac.jp/pub/Linux/ubuntu/
http://ftp.kfki.hu/linux/ubuntu/
http://ftp.linux.org.tr/ubuntu/
http://ftp.litnet.lt/ubuntu/
http://ftp.lysator.liu.se/ubuntu/
http://ftp.mtu.ru/pub/ubuntu/archive/
http://ftp.ncnu.edu.tw/Linux/ubuntu/ubuntu/
http://ftp.neowiz.com/ubuntu/
http://ftp.nluug.nl/os/Linux/distr/ubuntu/
http://ftp.nsysu.edu.tw/Ubuntu/ubuntu/
http://ftp.ntua.gr/pub/linux/ubuntu/
http://ftp.oleane.net/ubuntu/
http://ftp.psu.ac.th/pub/ubuntu/
http://ftp.riken.jp/Linux/ubuntu/
http://ftp.roedu.net/mirrors/ubuntulinux.org/ubuntu/
http://ftp.rrzn.uni-hannover.de/pub/mirror/linux/ubuntu/
http://ftp.rz.tu-bs.de/pub/mirror/ubuntu-packages/
http://ftp.snt.utwente.nl/pub/os/linux/ubuntu/
http://ftp.stust.edu.tw/pub/Linux/ubuntu/
http://ftp.stw-bonn.de/ubuntu/
http://ftp.sun.ac.za/ftp/ubuntu/
http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/
http://ftp.tc.edu.tw/Linux/ubuntu/
http://ftp.tecnoera.com/ubuntu/
http://ftp.telfort.nl/pub/mirror/ubuntu/
http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/
http://ftp.tku.edu.tw/ubuntu/
http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu/
http://ftp.tu-chemnitz.de/pub/linux/ubuntu-ports/
http://ftp.tu-chemnitz.de/pub/linux/ubuntu/
http://ftp.tu-ilmenau.de/mirror/ubuntu/
http://ftp.tudelft.nl/archive.ubuntu.com/
http://ftp.twaren.net/Linux/Ubuntu/ubuntu/
http://ftp.u-picardie.fr/mirror/ubuntu/ubuntu/
http://ftp.ubuntu-tw.net/mirror/ubuntu/
http://ftp.udc.es/ubuntu/
http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/
http://ftp.uni-kassel.de/ubuntu/ubuntu/
http://ftp.uni-kl.de/pub/linux/ubuntu/
http://ftp.uni-mainz.de/ubuntu/
http://ftp.unina.it/pub/linux/distributions/ubuntu/
http://ftp.uninett.no/ubuntu/
http://ftp.usf.edu/pub/ubuntu/
http://ftp.ussg.iu.edu/linux/ubuntu/
http://ftp.utexas.edu/ubuntu/
http://ftp.vectranet.pl/ubuntu/
http://ftp.wa.co.za/pub/ubuntu/ubuntu/
http://ftp.wcss.pl/ubuntu/
http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/archives/
http://ftp5.gwdg.de/pub/linux/debian/ubuntu/
http://ga.archive.ubuntu.com/ubuntu/
http://gaosu.rave.org/ubuntu/
http://gb.archive.ubuntu.com/ubuntu/
http://gd.archive.ubuntu.com/ubuntu/
http://gd.tuwien.ac.at/opsys/linux/ubuntu/archive/
http://ge.archive.ubuntu.com/ubuntu/
http://gf.archive.ubuntu.com/ubuntu/
http://gg.archive.ubuntu.com/ubuntu/
http://gh.archive.ubuntu.com/ubuntu/
http://gi.archive.ubuntu.com/ubuntu/
http://giano.com.dist.unige.it/ubuntu/
http://gl.archive.ubuntu.com/ubuntu/
http://gm.archive.ubuntu.com/ubuntu/
http://gn.archive.ubuntu.com/ubuntu/
http://gp.archive.ubuntu.com/ubuntu/
http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu/
http://gq.archive.ubuntu.com/ubuntu/
http://gr.archive.ubuntu.com/ubuntu/
http://gs.archive.ubuntu.com/ubuntu/
http://gt.archive.ubuntu.com/ubuntu/
http://gu.archive.ubuntu.com/ubuntu/
http://gw.archive.ubuntu.com/ubuntu/
http://gy.archive.ubuntu.com/ubuntu/
http://hk.archive.ubuntu.com/ubuntu/
http://hm.archive.ubuntu.com/ubuntu/
http://hn.archive.ubuntu.com/ubuntu/
http://hr.archive.ubuntu.com/ubuntu/
http://ht.archive.ubuntu.com/ubuntu/
http://hu.archive.ubuntu.com/ubuntu/
http://id.archive.ubuntu.com/ubuntu/
http://ie.archive.ubuntu.com/ubuntu/
http://il.archive.ubuntu.com/ubuntu/
http://im.archive.ubuntu.com/ubuntu/
http://in.archive.ubuntu.com/ubuntu/
http://io.archive.ubuntu.com/ubuntu/
http://iq.archive.ubuntu.com/ubuntu/
http://ir.archive.ubuntu.com/ubuntu/
http://is.archive.ubuntu.com/ubuntu/
http://it.archive.ubuntu.com/ubuntu/
http://jaran.undip.ac.id/ubuntu/
http://je.archive.ubuntu.com/ubuntu/
http://jm.archive.ubuntu.com/ubuntu/
http://jo.archive.ubuntu.com/ubuntu/
http://jp.archive.ubuntu.com/ubuntu/
http://kambing.ui.ac.id/ubuntu/
http://kartolo.sby.datautama.net.id/ubuntu/
http://ke.archive.ubuntu.com/ubuntu/
http://kebo.vlsm.org/ubuntu/
http://kg.archive.ubuntu.com/ubuntu/
http://kh.archive.ubuntu.com/ubuntu/
http://ki.archive.ubuntu.com/ubuntu/
http://km.archive.ubuntu.com/ubuntu/
http://kn.archive.ubuntu.com/ubuntu/
http://kp.archive.ubuntu.com/ubuntu/
http://kr.archive.ubuntu.com/ubuntu/
http://kw.archive.ubuntu.com/ubuntu/
http://ky.archive.ubuntu.com/ubuntu/
http://kz.archive.ubuntu.com/ubuntu/
http://la.archive.ubuntu.com/ubuntu/
http://lb.archive.ubuntu.com/ubuntu/
http://lc.archive.ubuntu.com/ubuntu/
http://li.archive.ubuntu.com/ubuntu/
http://linux.nsu.ru/ubuntu/
http://linux.psu.ru/ubuntu/
http://linux.vlz.su/ubuntu/
http://linux.xjtuns.cn/ubuntu/
http://lk.archive.ubuntu.com/ubuntu/
http://lr.archive.ubuntu.com/ubuntu/
http://ls.archive.ubuntu.com/ubuntu/
http://lt.archive.ubuntu.com/ubuntu/
http://lu.archive.ubuntu.com/ubuntu/
http://lug.mtu.edu/ubuntu/
http://lv.archive.ubuntu.com/ubuntu/
http://ly.archive.ubuntu.com/ubuntu/
http://ma.archive.ubuntu.com/ubuntu/
http://mc.archive.ubuntu.com/ubuntu/
http://md.archive.ubuntu.com/ubuntu/
http://me.archive.ubuntu.com/ubuntu/
http://mf.archive.ubuntu.com/ubuntu/
http://mg.archive.ubuntu.com/ubuntu/
http://mh.archive.ubuntu.com/ubuntu/
http://mirror-fpt-telecom.fpt.net/ubuntu/
http://mirror.1000mbps.com/ubuntu/
http://mirror.aarnet.edu.au/pub/ubuntu/archive/
http://mirror.alfredstate.edu/ubuntu/
http://mirror.ancl.hawaii.edu/linux/ubuntu/
http://mirror.anl.gov/pub/ubuntu/
http://mirror.aptus.co.tz/pub/ubuntuarchive/
http://mirror.arlug.ro/pub/ubuntu/ubuntu/
http://mirror.as24220.net/pub/ubuntu-archive/
http://mirror.as24220.net/pub/ubuntu/
http://mirror.as29550.net/archive.ubuntu.com/
http://mirror.as43289.net/ubuntu/
http://mirror.bauhuette.fh-aachen.de/ubuntu/
http://mirror.beget.ru/ubuntu/
http://mirror.bjtu.edu.cn/ubuntu/
http://mirror.blizoo.mk/ubuntu/
http://mirror.bytemark.co.uk/ubuntu/
http://mirror.calvin.edu/ubuntu/
http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/
http://mirror.cc.vt.edu/pub2/ubuntu/
http://mirror.clarkson.edu/ubuntu/
http://mirror.clibre.uqam.ca/ubuntu/
http://mirror.cogentco.com/pub/linux/ubuntu/
http://mirror.corbina.net/ubuntu/
http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/
http://mirror.crazynetwork.it/ubuntu/archive/
http://mirror.cs.umn.edu/ubuntu/
http://mirror.csclub.uwaterloo.ca/ubuntu/
http://mirror.cse.iitk.ac.in/ubuntu/
http://mirror.datacenter.by/ubuntu/
http://mirror.datacenter.mn/ubuntu/
http://mirror.de.leaseweb.net/ubuntu/
http://mirror.dhakacom.com/ubuntu-archive/
http://mirror.dhakacom.com/ubuntu/
http://mirror.easyspeedy.com/ubuntu/
http://mirror.edatel.net.co/ubuntu/
http://mirror.euserv.net/linux/ubuntu/
http://mirror.fcaglp.unlp.edu.ar/ubuntu/
http://mirror.globo.com/ubuntu/archive/
http://mirror.greennet.gl/ubuntu/
http://mirror.hmc.edu/ubuntu/
http://mirror.i3d.net/pub/ubuntu/
http://mirror.internode.on.net/pub/ubuntu/ubuntu/
http://mirror.isoc.org.il/pub/ubuntu/
http://mirror.it.ubc.ca/ubuntu/
http://mirror.its.dal.ca/ubuntu/
http://mirror.its.sfu.ca/mirror/ubuntu/
http://mirror.jmu.edu/pub/ubuntu/
http://mirror.kavalinux.com/ubuntu/
http://mirror.kku.ac.th/ubuntu/
http://mirror.krystal.co.uk/ubuntu/
http://mirror.lagoon.nc/ubuntu/
http://mirror.lcsee.wvu.edu/ubuntu/
http://mirror.learn.ac.lk/ubuntu/
http://mirror.lstn.net/ubuntu/
http://mirror.lupaworld.com/ubuntu/
http://mirror.lzu.edu.cn/ubuntu/
http://mirror.math.ucdavis.edu/ubuntu/
http://mirror.metrocast.net/ubuntu/
http://mirror.mirohost.net/ubuntu/
http://mirror.mythic-beasts.com/ubuntu/
http://mirror.neolabs.kz/ubuntu/
http://mirror.netcologne.de/ubuntu/
http://mirror.netlinux.cl/ubuntu/
http://mirror.neu.edu.cn/ubuntu/
http://mirror.nexcess.net/ubuntu/
http://mirror.nhanhoa.com/Ubuntu/archive/
http://mirror.nl.leaseweb.net/ubuntu/
http://mirror.nus.edu.sg/ubuntu/
http://mirror.optus.net/ubuntu/
http://mirror.oscc.org.my/ubuntu/
http://mirror.overthewire.com.au/ubuntu/
http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/
http://mirror.peer1.net/ubuntu/
http://mirror.picosecond.org/ubuntu/
http://mirror.pnl.gov/ubuntu/
http://mirror.pregi.net/ubuntu/
http://mirror.premi.st/ubuntu/
http://mirror.rol.ru/ubuntu/
http://mirror.serverloft.eu/ubuntu/ubuntu/
http://mirror.siamdata.co.th/ubuntu/
http://mirror.skylink-datacenter.de/ubuntu/
http://mirror.skyshe.com/ubuntu/
http://mirror.soften.ktu.lt/ubuntu/
http://mirror.sov.uk.goscomb.net/ubuntu/
http://mirror.squ.edu.om/ubuntuarchive/
http://mirror.steadfast.net/ubuntu/
http://mirror.switch.ch/ftp/mirror/ubuntu/
http://mirror.symnds.com/ubuntu/
http://mirror.tcpdiag.net/ubuntu/
http://mirror.team-cymru.org/ubuntu/
http://mirror.telepoint.bg/ubuntu/
http://mirror.thelinuxfix.com/ubuntu/
http://mirror.timeweb.ru/ubuntu/
http://mirror.tocici.com/ubuntu/
http://mirror.ubuntu.ikoula.com/ubuntu/
http://mirror.uchile.cl/ubuntu/
http://mirror.umd.edu/ubuntu/
http://mirror.unej.ac.id/ubuntu/
http://mirror.unesp.br/ubuntu/
http://mirror.unix-solutions.be/ubuntu/
http://mirror.uoregon.edu/ubuntu/
http://mirror.us.leaseweb.net/ubuntu/
http://mirror.vcu.edu/pub/gnu+linux/ubuntu/
http://mirror.waia.asn.au/ubuntu/
http://mirror.xnet.co.nz/pub/ubuntu/
http://mirror.yandex.ru/ubuntu/
http://mirror.zol.co.zw/ubuntu/
http://mirror1.ku.ac.th/ubuntu/
http://mirror2.corbina.ru/ubuntu/
http://mirror2.tuxinator.org/ubuntu/
http://mirrors.163.com/ubuntu/
http://mirrors.accretive-networks.net/ubuntu/
http://mirrors.acm.jhu.edu/ubuntu/
http://mirrors.advancedhosters.com/ubuntu/
http://mirrors.arpnetworks.com/Ubuntu/
http://mirrors.bloomu.edu/ubuntu/
http://mirrors.cat.pdx.edu/ubuntu/
http://mirrors.ccs.neu.edu/ubuntu/
http://mirrors.coreix.net/ubuntu/
http://mirrors.digipower.vn/ubuntu/archive/
http://mirrors.dotsrc.org/ubuntu/
http://mirrors.einstein.yu.edu/ubuntu/archive/
http://mirrors.fe.up.pt/ubuntu/
http://mirrors.gigenet.com/ubuntuarchive/
http://mirrors.hust.edu.cn/ubuntu/
http://mirrors.hustunique.com/ubuntu/
http://mirrors.ircam.fr/pub/ubuntu/archive/
http://mirrors.ispros.com.bd/ubuntu/
http://mirrors.manchester.m247.com/ubuntu/
http://mirrors.melbourne.co.uk/ubuntu/
http://mirrors.mit.edu/ubuntu/
http://mirrors.neterra.net/ubuntu/
http://mirrors.nfsi.pt/ubuntu/
http://mirrors.nic.funet.fi/ubuntu/
http://mirrors.nl.eu.kernel.org/ubuntu/
http://mirrors.oss.org.cn/ubuntu/
http://mirrors.psu.ac.th/ubuntu/
http://mirrors.rit.edu/ubuntu/
http://mirrors.se.eu.kernel.org/ubuntu/
http://mirrors.shlug.org/ubuntu/
http://mirrors.sohu.com/ubuntu/
http://mirrors.syringanetworks.net/ubuntu-archive/
http://mirrors.telianet.dk/ubuntu/
http://mirrors.uaip.org/ubuntu/
http://mirrors.us.kernel.org/ubuntu/
http://mirrors.usinternet.com/ubuntu/archive/
http://mirrors.ustc.edu.cn/ubuntu/
http://mirrors.xmission.com/ubuntu/
http://mirrors.yun-idc.com/ubuntu/
http://mirrors.zju.edu.cn/ubuntu/
http://mk.archive.ubuntu.com/ubuntu/
http://ml.archive.ubuntu.com/ubuntu/
http://mm.archive.ubuntu.com/ubuntu/
http://mn.archive.ubuntu.com/ubuntu/
http://mo.archive.ubuntu.com/ubuntu/
http://mp.archive.ubuntu.com/ubuntu/
http://mq.archive.ubuntu.com/ubuntu/
http://mr.archive.ubuntu.com/ubuntu/
http://ms.archive.ubuntu.com/ubuntu/
http://mt.archive.ubuntu.com/ubuntu/
http://mu.archive.ubuntu.com/ubuntu/
http://mv.archive.ubuntu.com/ubuntu/
http://mw.archive.ubuntu.com/ubuntu/
http://mx.archive.ubuntu.com/ubuntu/
http://my.archive.ubuntu.com/ubuntu/
http://mz.archive.ubuntu.com/ubuntu/
http://na.archive.ubuntu.com/ubuntu/
http://nc.archive.ubuntu.com/ubuntu/
http://ne.archive.ubuntu.com/ubuntu/
http://nf.archive.ubuntu.com/ubuntu/
http://ng.archive.ubuntu.com/ubuntu/
http://ni.archive.ubuntu.com/ubuntu/
http://nl.archive.ubuntu.com/ubuntu/
http://nl3.archive.ubuntu.com/ubuntu/
http://no.archive.ubuntu.com/ubuntu/
http://np.archive.ubuntu.com/ubuntu/
http://nr.archive.ubuntu.com/ubuntu/
http://nu.archive.ubuntu.com/ubuntu/
http://nz.archive.ubuntu.com/ubuntu/
http://om.archive.ubuntu.com/ubuntu/
http://osmirror.rug.nl/ubuntu/
http://pa.archive.ubuntu.com/ubuntu/
http://pandawa.ipb.ac.id/ubuntu/
http://pe.archive.ubuntu.com/ubuntu/
http://pf.archive.ubuntu.com/ubuntu/
http://pg.archive.ubuntu.com/ubuntu/
http://ph.archive.ubuntu.com/ubuntu/
http://piotrkosoft.net/pub/mirrors/ubuntu/
http://pl.archive.ubuntu.com/ubuntu/
http://pm.archive.ubuntu.com/ubuntu/
http://pn.archive.ubuntu.com/ubuntu/
http://pr.archive.ubuntu.com/ubuntu/
http://ps.archive.ubuntu.com/ubuntu/
http://pt.archive.ubuntu.com/ubuntu/
http://pw.archive.ubuntu.com/ubuntu/
http://py.archive.ubuntu.com/ubuntu/
http://qa.archive.ubuntu.com/ubuntu/
http://re.archive.ubuntu.com/ubuntu/
http://repo.undip.ac.id/ubuntu/
http://ro.archive.ubuntu.com/ubuntu/
http://rs.archive.ubuntu.com/ubuntu/
http://ru.archive.ubuntu.com/ubuntu/
http://rw.archive.ubuntu.com/ubuntu/
http://sa.archive.ubuntu.com/ubuntu/
http://sb.archive.ubuntu.com/ubuntu/
http://sc.archive.ubuntu.com/ubuntu/
http://sd.archive.ubuntu.com/ubuntu/
http://se.archive.ubuntu.com/ubuntu/
http://sft.if.usp.br/ubuntu/
http://sg.archive.ubuntu.com/ubuntu/
http://sh.archive.ubuntu.com/ubuntu/
http://shadow.ind.ntou.edu.tw/ubuntu/
http://si.archive.ubuntu.com/ubuntu/
http://sj.archive.ubuntu.com/ubuntu/
http://sk.archive.ubuntu.com/ubuntu/
http://sl.archive.ubuntu.com/ubuntu/
http://sm.archive.ubuntu.com/ubuntu/
http://sn.archive.ubuntu.com/ubuntu/
http://so.archive.ubuntu.com/ubuntu/
http://speglar.simnet.is/ubuntu/
http://sr.archive.ubuntu.com/ubuntu/
http://ss.archive.ubuntu.com/ubuntu/
http://st.archive.ubuntu.com/ubuntu/
http://stingray.cyber.net.pk/pub/ubuntu/
http://su.archive.ubuntu.com/ubuntu/
http://sunsite.rediris.es/mirror/ubuntu-archive/
http://suro.ubaya.ac.id/ubuntu/
http://suse.uni-leipzig.de/pub/releases.ubuntu.com/ubuntu/
http://sv.archive.ubuntu.com/ubuntu/
http://sx.archive.ubuntu.com/ubuntu/
http://sy.archive.ubuntu.com/ubuntu/
http://sz.archive.ubuntu.com/ubuntu/
http://tc.archive.ubuntu.com/ubuntu/
http://td.archive.ubuntu.com/ubuntu/
http://tezcatl.fciencias.unam.mx/ubuntu/
http://tf.archive.ubuntu.com/ubuntu/
http://tg.archive.ubuntu.com/ubuntu/
http://th.archive.ubuntu.com/ubuntu/
http://tj.archive.ubuntu.com/ubuntu/
http://tk.archive.ubuntu.com/ubuntu/
http://tl.archive.ubuntu.com/ubuntu/
http://tm.archive.ubuntu.com/ubuntu/
http://tn.archive.ubuntu.com/ubuntu/
http://to.archive.ubuntu.com/ubuntu/
http://tp.archive.ubuntu.com/ubuntu/
http://tr.archive.ubuntu.com/ubuntu/
http://tt.archive.ubuntu.com/ubuntu/
http://tux.rainside.sk/ubuntu/
http://tv.archive.ubuntu.com/ubuntu/
http://tw.archive.ubuntu.com/ubuntu/
http://tz.archive.ubuntu.com/ubuntu/
http://ua.archive.ubuntu.com/ubuntu/
http://ubuntu-arch.linux.edu.lv/ubuntu/
http://ubuntu-archive.locaweb.com.br/ubuntu/
http://ubuntu-archive.mirror.nucleus.be/
http://ubuntu-archive.mirror.serveriai.lt/
http://ubuntu-archive.mirrors.free.org/ubuntu/
http://ubuntu-archive.mirrors.proxad.net/ubuntu/
http://ubuntu-archive.polytechnic.edu.na/ubuntu/
http://ubuntu-archives.mirror.nexicom.net/
http://ubuntu-ashisuto.ubuntulinux.jp/ubuntu/
http://ubuntu-mirror.neocom.org.ua/ubuntu/
http://ubuntu-mirror.telesys.org.ua/ubuntu/
http://ubuntu-mirror.totbb.net/ubuntu/
http://ubuntu.01link.hk/
http://ubuntu.bhs.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/
http://ubuntu.c3sl.ufpr.br/ubuntu/
http://ubuntu.cica.es/ubuntu/
http://ubuntu.cn99.com/ubuntu/
http://ubuntu.cnssuestc.org/ubuntu/
http://ubuntu.cs.nctu.edu.tw/ubuntu/
http://ubuntu.cs.utah.edu/ubuntu/
http://ubuntu.ctu.edu.vn/archive/
http://ubuntu.cybercomhosting.com/ubuntu/
http://ubuntu.datahop.net/ubuntu/
http://ubuntu.dcc.fc.up.pt/
http://ubuntu.dormforce.net/ubuntu/
http://ubuntu.dts.mg/ubuntu/
http://ubuntu.etf.bg.ac.rs/ubuntu/
http://ubuntu.excellmedia.net/archive/
http://ubuntu.fastbull.org/ubuntu/
http://ubuntu.gnu.gen.tr/ubuntu/
http://ubuntu.grena.ge/ubuntu/
http://ubuntu.grn.cat/ubuntu/
http://ubuntu.ictvalleumbra.it/ubuntu/
http://ubuntu.indika.net.id/ubuntu/
http://ubuntu.inode.at/ubuntu/
http://ubuntu.ip-connect.vn.ua/
http://ubuntu.ipacct.com/ubuntu/
http://ubuntu.koyanet.lv/ubuntu/
http://ubuntu.lagis.at/ubuntu/
http://ubuntu.laps.ufpa.br/ubuntu/
http://ubuntu.linux-bg.org/ubuntu/
http://ubuntu.mirror.ac.ke/ubuntu/
http://ubuntu.mirror.atratoip.net/ubuntu/
http://ubuntu.mirror.cambrium.nl/ubuntu/
http://ubuntu.mirror.constant.com/
http://ubuntu.mirror.crucial.com.au/
http://ubuntu.mirror.frontiernet.net/ubuntu/
http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/
http://ubuntu.mirror.gtcomm.net/ubuntu/
http://ubuntu.mirror.iweb.ca/
http://ubuntu.mirror.lrz.de/ubuntu/
http://ubuntu.mirror.neology.co.za/ubuntu/
http://ubuntu.mirror.pop-sc.rnp.br/ubuntu/
http://ubuntu.mirror.rafal.ca/ubuntu/
http://ubuntu.mirror.root.lu/ubuntu/
http://ubuntu.mirror.serversaustralia.com.au/ubuntu/
http://ubuntu.mirror.su.se/ubuntu/
http://ubuntu.mirror.tn/
http://ubuntu.mirror.tudos.de/ubuntu/
http://ubuntu.mirror.uber.com.au/archive/
http://ubuntu.mirror.vu.lt/ubuntu/
http://ubuntu.mirrors.crysys.hu/
http://ubuntu.mirrors.isu.net.sa/ubuntu/
http://ubuntu.mirrors.linux.ro/archive/
http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/
http://ubuntu.mirrors.skynet.be/pub/ubuntu.com/ubuntu/
http://ubuntu.mirrors.skynet.be/ubuntu/
http://ubuntu.mirrors.tds.net/pub/ubuntu/
http://ubuntu.mirrors.uk2.net/ubuntu/
http://ubuntu.ntc.net.np/ubuntu/
http://ubuntu.org.ua/ubuntu/
http://ubuntu.osuosl.org/ubuntu/
http://ubuntu.otenet.gr/
http://ubuntu.pesat.net.id/archive/
http://ubuntu.positive-internet.com/ubuntu/
http://ubuntu.retrosnub.co.uk/ubuntu/
http://ubuntu.saix.net/ubuntu-archive/
http://ubuntu.securedservers.com/
http://ubuntu.serverspace.co.uk/ubuntu/
http://ubuntu.skarta.net/ubuntu/
http://ubuntu.skybroadband.com.ph/ubuntu/
http://ubuntu.snet.uz/ubuntu/
http://ubuntu.sth.sze.hu/ubuntu/
http://ubuntu.stu.edu.tw/ubuntu/
http://ubuntu.task.gda.pl/ubuntu/
http://ubuntu.tiscali.nl/
http://ubuntu.trumpetti.atm.tut.fi/ubuntu/
http://ubuntu.tsl.gr/
http://ubuntu.tuxuri.com/ubuntu/
http://ubuntu.uc3m.es/ubuntu/
http://ubuntu.ucr.ac.cr/ubuntu/
http://ubuntu.uestc.edu.cn/ubuntu/
http://ubuntu.ufes.br/ubuntu-archive/
http://ubuntu.uhost.hk/
http://ubuntu.uib.no/archive/
http://ubuntu.unc.edu.ar/ubuntu/
http://ubuntu.uni-klu.ac.at/ubuntu/
http://ubuntu.unitedcolo.de/ubuntu/
http://ubuntu.univ-nantes.fr/ubuntu/
http://ubuntu.univ-reims.fr/ubuntu/
http://ubuntu.virginmedia.com/archive/
http://ubuntu.volia.net/ubuntu-archive/
http://ubuntu.wallawalla.edu/ubuntu/
http://ubuntu.wikimedia.org/ubuntu/
http://ubuntuarchive.mirror.nac.net/
http://ubuntutym.u-toyama.ac.jp/ubuntu/
http://ucho.ignum.cz/ubuntu/
http://ucmirror.canterbury.ac.nz/ubuntu/
http://ug.archive.ubuntu.com/ubuntu/
http://uk.archive.ubuntu.com/ubuntu/
http://um.archive.ubuntu.com/ubuntu/
http://us.archive.ubuntu.com/ubuntu/
http://uy.archive.ubuntu.com/ubuntu/
http://uz.archive.ubuntu.com/ubuntu/
http://va.archive.ubuntu.com/ubuntu/
http://vc.archive.ubuntu.com/ubuntu/
http://ve.archive.ubuntu.com/ubuntu/
http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/
http://vg.archive.ubuntu.com/ubuntu/
http://vi.archive.ubuntu.com/ubuntu/
http://vn.archive.ubuntu.com/ubuntu/
http://vu.archive.ubuntu.com/ubuntu/
http://wf.archive.ubuntu.com/ubuntu/
http://ws.archive.ubuntu.com/ubuntu/
http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/
http://www.club.cc.cmu.edu/pub/ubuntu/
http://www.ftp.ne.jp/Linux/packages/ubuntu/archive/
http://www.gtlib.gatech.edu/pub/ubuntu/
http://www.las.ic.unicamp.br/pub/ubuntu/
http://www.lug.bu.edu/mirror/ubuntu/
http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/
http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/
http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/
http://ye.archive.ubuntu.com/ubuntu/
http://yt.archive.ubuntu.com/ubuntu/
http://za.archive.ubuntu.com/ubuntu/
http://zm.archive.ubuntu.com/ubuntu/
http://zw.archive.ubuntu.com/ubuntu/

```

It seems easy enough to implement:
```
 PrecacheFor: uburep/dists/trusty/  uburep/dists/trusty-updates/  uburep/dists/trusty-security/ uburep/dists/vivid/  uburep/dists/vivid-updates/  uburep/dists/vivid-security/ uburep/dists/wily/  uburep/dists/wily-updates/  uburep/dists/wily-security/ 
```
Am I missing anything? I'm worried incorrectly implementing this will destroy the present cache.

---

