---
title: "Problem install drivers for Tplink tx201"
date: 2023-02-18
forum: Server Platforms
---

### Post by damien455 on 2023-02-18
[COLOR=#1C1C1C][FONT=&quot]Using Ubuntu server 22.04.1 trying to install a 2.5Gb TPlink tx201[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot][https://www.tp-link.com/en/support/download/tx201/](https://www.tp-link.com/en/support/download/tx201/)[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]using the instructions here[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot][https://www.tp-link.com/en/support/faq/3435/](https://www.tp-link.com/en/support/faq/3435/)[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]when running the [autorun.sh]("https://autorun.sh/") getting the following message[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]Check old driver and unload it.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]Build the module and install[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]warning: the compiler differs from the one used to build the kernel[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.2.0-3ubuntu1) 12.2.0[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]You are using: gcc (Ubuntu 12.2.0-3ubuntu1) 12.2.0[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]/home/damien/r8125-9.009.01/src/r8125_n.c: In function ‘rtl8125_init_board’:[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]/home/damien/r8125-9.009.01/src/r8125_n.c:11955:14: error: implicit declaration of function ‘pci_set_dma_mask’ [-Werror=implicit-function-declaration][/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]11955 | !pci_set_dma_mask(pdev, DMA_BIT_MASK(64)) &&[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]| ^~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]/home/damien/r8125-9.009.01/src/r8125_n.c:11956:14: error: implicit declaration of function ‘pci_set_consistent_dma_mask’ [-Werror=implicit-function-declaration][/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]11956 | !pci_set_consistent_dma_mask(pdev, DMA_BIT_MASK(64))) {[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]| ^~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]/home/damien/r8125-9.009.01/src/r8125_n.c: In function ‘rtl8125_init_one’:[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]/home/damien/r8125-9.009.01/src/r8125_n.c:12718:17: error: implicit declaration of function ‘netif_set_gso_max_size’; did you mean ‘netif_set_tso_max_size’? [-Werror=implicit-function-declaration][/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]12718 | netif_set_gso_max_size(dev, LSO_64K);[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]| ^~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]| netif_set_tso_max_size[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]cc1: some warnings being treated as errors[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]make[3]: *** [scripts/Makefile.build:257: /home/damien/r8125-9.009.01/src/r8125_n.o] Error 1[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]make[2]: *** [Makefile:1850: /home/damien/r8125-9.009.01/src] Error 2[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]make[1]: *** [Makefile:176: modules] Error 2[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]make: *** [Makefile:41: modules] Error 2[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]
[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-02-20
Please post the results of 
[code]
uname -r
lsb_release -d
[code]
I ask because of th notes in the driver download page
> 

[TABLE="class: download-resource-table"]
[TR="class: basic-info"]
[TH="class: download-resource-name, colspan: 2"]TX201_V1_Linux
                         [/TH]
                         [TH="class: download-resource-btnbox"]                           [Download]("https://static.tp-link.com/upload/software/2022/202206/20220623/TX201(UN) 1.0 Linux driver-9.009.01.bz2")                         [/TH]
                       [/TR]
                       [TR="class: detail-info"]
                         [TD]                           Published Date: 2022-06-23                          [/TD]
                         [TD]                           Language:  English                          [/TD]
                         [TD]                           File Size: 87.79 KB                          [/TD]
                       [/TR]
                                                                   [TR="class: detail-info"]
                         [TD="class: os, colspan: 3"]Operating System: Linux kernal 5.17
[/TD]
                       [/TR]
                                             [TR="class: more-info"]
                         [TD="class: more, colspan: 3"]                                                                                                                                                 
                             Notes:
1. [COLOR=#ff0000]For Linux kernel up to 5.17[/COLOR].
2. For TX201(UN) V1.0.

                           
[/TD]
[/TR]
[/TABLE]

Current today in 22.04.1 is Linux Kernel 5.19.0-32... Just saying.

---

