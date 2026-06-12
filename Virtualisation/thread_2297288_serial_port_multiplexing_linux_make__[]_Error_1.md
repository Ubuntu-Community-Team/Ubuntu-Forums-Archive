---
title: "serial port multiplexing linux make: *** [] Error 1"
date: 2015-10-02
forum: Virtualisation
---

### Post by bobdxcool on 2015-10-02
[FONT=Helvetica Neue]I am on a ubunto 12.0.4 LTS OS. I am trying to implement CMUX multiplexing protocol on the serial port to which I have a serial GSM modem connected. I was following instructions this page,[http://source.sierrawireless.com/resources/sagemcomm2m/hilo/mux_07,-d-,10_linux_implementation_for_hilo_and_hilonc/](http://source.sierrawireless.com/resources/sagemcomm2m/hilo/mux_07,-d-,10_linux_implementation_for_hilo_and_hilonc/)[/FONT]
[FONT=Helvetica Neue]where I downloaded a zip file which C programs to implement. Zip file uploaded here,[https://www.dropbox.com/s/lbr5k2ln6ec3904/MUX_0710_Guidelines_and_Sources.zip?dl=0](https://www.dropbox.com/s/lbr5k2ln6ec3904/MUX_0710_Guidelines_and_Sources.zip?dl=0)[/FONT]
[FONT=Helvetica Neue]As per the instructions there, I have to download sudo apt-get install qt4-make . But,I am not able to download this on my ubuntu OS 12.0.4 LTS. It says cannot locate package.[/FONT]
[FONT=Helvetica Neue]In the serial signals folder attached in the zip above, I have to execute qmake SerialSignals.pro, which works and this is the output,[/FONT]
[FONT=Helvetica Neue]/Desktop/sierra/gsmMUX/AppliMux/SerialSignals# qmake SerialSignals.pro

[/FONT]
[COLOR=#000000]uic[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#2B91AF]File[/COLOR][COLOR=#000000] generated [/COLOR][COLOR=#00008B]with[/COLOR][COLOR=#000000] too old version of [/COLOR][COLOR=#2B91AF]Qt[/COLOR][COLOR=#2B91AF]Designer[/COLOR][COLOR=#000000]([/COLOR][COLOR=#800000]3.3[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000] 

[/COLOR][FONT=Helvetica Neue]After doing I am supposed to execute the make command. When I type in make, the output is

[/FONT]
[COLOR=#2B91AF]File[/COLOR][COLOR=#800000]'SerialSignals.ui'[/COLOR][COLOR=#00008B]is[/COLOR][COLOR=#00008B]not[/COLOR][COLOR=#000000] valid
make[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000]***[/COLOR][COLOR=#000000][.[/COLOR][COLOR=#000000]ui[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]ui_SerialSignals[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]h[/COLOR][COLOR=#000000]][/COLOR][COLOR=#2B91AF]Error[/COLOR][COLOR=#800000]1[/COLOR][FONT=Helvetica Neue]
How do I resolve this ?
How do I need to install qt4-make ? Is this required for compilation ?[/FONT]

---

