---
title: "[SOLVED] red entre 2 PCs con Ubuntu"
date: 2009-06-05
forum: Software
---

### Post by leosr on 2009-06-05
Hola.
Reviví una máquina vieja, Celeron (Coppermine) con 256 mb Ram compartido con la placa de video y un HD de 19 Gb, le instalé Xubuntu Jaunty y funciona relativamente bien.
Ahora bien... quiero conectarla en red con mi otra PC para compartir archivos e impresoras (conectadas a esta última). Esta máquina tiene instalado Ubuntu Jaunty. Las 2 están conectadas por medio de un router ADSL por el cual comparten internet (que funciona en ambas). Leí el siguiente tutorial: [http://ubuntu-ar.org/tutoriales/samba](http://ubuntu-ar.org/tutoriales/samba)
La cosa es que no me funcionó, no sé que estoy haciendo mal. El tutorial es válido para Ubuntu/Xubuntu Jaunty?

Cómo hago en XFCE para conectarme a una máquina de red?

Es normal que XFCE baje muchos paquetes de Gnome? Nunca usé XFCE.

Aclaración: las 2 máquinas están formateadas con ext4.

Saludos.

---

### Post by staar on 2009-06-05
para que usar samba si ambas tienen linux? usa NFS, samba es para el protocolo SMB de M$, NFS es el equivalente nativo...

saludos

---

### Post by leosr on 2009-06-05
> **staar said:**
> para que usar samba si ambas tienen linux? usa NFS, samba es para el protocolo SMB de M$, NFS es el equivalente nativo...

saludos

ok, cómo se configura?

---

### Post by guillermolisi on 2009-06-05
> **leosr said:**
> ok, cómo se configura?

[Asi]("http://ubuntu-ar.org/node/208")

---

### Post by juancarlospaco on 2009-06-05
Pero con 256 de ram podes instalarle Ubuntu con Gnome, pero usa el Alternate CD, 
el instalador basado en texto, asi te quedan todos los desktop igual.

Usa NFS.

---

### Post by staar on 2009-06-05
[http://ubuntu-ar.org/node/208]("http://ubuntu-ar.org/node/208") <-- Tuto de ubuntu-ar (ojo que usa vi como editor de texto, si te resulta dificil ese editor, cambialo por nano, mousepad, gedit)

[http://axlinux.blogspot.com/2007/08/compartir-impresoras-y-archivos-en.html]("http://axlinux.blogspot.com/2007/08/compartir-impresoras-y-archivos-en.html") <-- para la impresora


más de NFS:

[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html")

[http://doc.ubuntu-es.org/NFS]("http://doc.ubuntu-es.org/NFS")

[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html")

[http://linuteca.com/comparte-archivos-con-nfs-en-ubuntu/]("http://linuteca.com/comparte-archivos-con-nfs-en-ubuntu/")

saludos

---

### Post by leosr on 2009-06-05
Cuando instalo NFS-kernel-server sale un error que al reiniciar la máquina la cuelga y sólo puedo volver a iniciarla al desinstalar el paquete.
Esta es la salida de la consola de Synaptic en la instalación:

---

### Post by leosr on 2009-06-05
lo mismo desde la terminal

---

### Post by leosr on 2009-06-05
Tendrá algo que ver que anteriormente estuve tratando de configurar SAMBA?

---

### Post by guillermolisi on 2009-06-06
> **leosr said:**
> Tendrá algo que ver que anteriormente estuve tratando de configurar SAMBA?
En principio no, porque tengo varias instalaciones donde funcionan simultaneamente Samba y NFS sin conflictos.

Que guia seguiste para instalar NFS de todas las que se pasaron ?

---

### Post by leosr on 2009-06-06
> **guillermolisi said:**
> En principio no, porque tengo varias instalaciones donde funcionan simultaneamente Samba y NFS sin conflictos.

Que guia seguiste para instalar NFS de todas las que se pasaron ?

Hola.

Primero lo instalé desde Synaptic, después lo quité y lo instalé desde la consola. En realidad no pude llegar más que a la instalación de NFS, en principio pensaba seguir la primer guía, la que me pasaste. Por lo que veo ahora estoy teniendo um problema con las dependencias. No sé cómo arreglarlo.
La 1º vez que lo instalé, cuando reinicié la PC se quedaba "congelada" cuando trataba de iniciar el servicio "NFS kernel daemon". Inicié en modo recovery y desde la consola ejecuté dpks -r y el nombre de los 2 paquetes instalados. Luego reinicié y arrancó con normalidad.
En los pantallazos se vé lo que aparace al instalar, que es lo mismo que me aparece al reiniciar la PC.
En la PC con Xubuntu NFS está instalado, no lo configuré todavía. Esa va a ser la máquina Cliente.

Será que tira ese error porque nfs no está configurado?

---

### Post by guillermolisi on 2009-06-06
> **leosr said:**
> Hola.

Primero lo instalé desde Synaptic, después lo quité y lo instalé desde la consola. En realidad no pude llegar más que a la instalación de NFS, en principio pensaba seguir la primer guía, la que me pasaste. Por lo que veo ahora estoy teniendo um problema con las dependencias. No sé cómo arreglarlo.
La 1º vez que lo instalé, cuando reinicié la PC se quedaba "congelada" cuando trataba de iniciar el servicio "NFS kernel daemon". Inicié en modo recovery y desde la consola ejecuté dpks -r y el nombre de los 2 paquetes instalados. Luego reinicié y arrancó con normalidad.
En los pantallazos se vé lo que aparace al instalar, que es lo mismo que me aparece al reiniciar la PC.
En la PC con Xubuntu NFS está instalado, no lo configuré todavía. Esa va a ser la máquina Cliente.

Será que tira ese error porque nfs no está configurado?
La instalacion via apt-get o Synaptic deberia resolver las dependencias.

NFS deberia correr fluidamente bien desde que terminas de instalarlo.

Cuando pasan cosas asi, lo mejor es buscar algun indicio en los logs, por lo menos en /var/log/messages y /var/log/dmesg.

NFS no necesita ser configurado mas alla de definir que recursos publicara en el server y cuales montara en el cliente.

---

### Post by leosr on 2009-06-06
Esto es lo que sale de /var/log/messages

Jun  6 07:45:54 Semprom2600-desktop syslogd 1.5.0#5ubuntu3: restart.
Jun  6 08:07:10 Semprom2600-desktop -- MARK --
Jun  6 08:27:10 Semprom2600-desktop -- MARK --
Jun  6 08:47:10 Semprom2600-desktop -- MARK --
Jun  6 09:07:10 Semprom2600-desktop -- MARK --
Jun  6 09:27:10 Semprom2600-desktop -- MARK --
Jun  6 09:47:10 Semprom2600-desktop -- MARK --
Jun  6 10:07:10 Semprom2600-desktop -- MARK --
Jun  6 10:27:10 Semprom2600-desktop -- MARK --
Jun  6 10:47:10 Semprom2600-desktop -- MARK --
Jun  6 11:07:10 Semprom2600-desktop -- MARK --
Jun  6 11:27:10 Semprom2600-desktop -- MARK --
Jun  6 11:47:10 Semprom2600-desktop -- MARK --
Jun  6 12:07:10 Semprom2600-desktop -- MARK --
Jun  6 12:27:10 Semprom2600-desktop -- MARK --
Jun  6 12:36:40 Semprom2600-desktop kernel: [59394.360487] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Jun  6 12:47:10 Semprom2600-desktop -- MARK --
Jun  6 12:53:18 Semprom2600-desktop kernel: [60392.443715] usblp1: removed
Jun  6 12:58:51 Semprom2600-desktop kernel: [60725.047878] usblp0: removed
Jun  6 13:27:10 Semprom2600-desktop -- MARK --
Jun  6 13:47:10 Semprom2600-desktop -- MARK --
Jun  6 14:07:10 Semprom2600-desktop -- MARK --
Jun  6 14:16:24 Semprom2600-desktop sudo: pam_sm_authenticate: Called 
Jun  6 14:16:24 Semprom2600-desktop sudo: pam_sm_authenticate: username = [leo] 
Jun  6 14:16:24 Semprom2600-desktop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jun  6 14:16:27 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 14:16:29 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 14:16:29 Semprom2600-desktop sudo: There is already a key in the user session keyring for the given passphrase. 
Jun  6 14:27:10 Semprom2600-desktop -- MARK --
Jun  6 14:47:10 Semprom2600-desktop -- MARK --
Jun  6 15:02:34 Semprom2600-desktop sudo: pam_sm_authenticate: Called 
Jun  6 15:02:34 Semprom2600-desktop sudo: pam_sm_authenticate: username = [leo] 
Jun  6 15:02:34 Semprom2600-desktop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jun  6 15:02:39 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 15:02:40 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 15:02:40 Semprom2600-desktop sudo: There is already a key in the user session keyring for the given passphrase. 
Jun  6 15:15:26 Semprom2600-desktop sudo: pam_sm_authenticate: Called 
Jun  6 15:15:26 Semprom2600-desktop sudo: pam_sm_authenticate: username = [leo] 
Jun  6 15:15:26 Semprom2600-desktop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jun  6 15:15:28 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 15:15:29 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 15:15:29 Semprom2600-desktop sudo: There is already a key in the user session keyring for the given passphrase. 
Jun  6 15:23:48 Semprom2600-desktop kernel: [69421.926770] RPC: Registered udp transport module.
Jun  6 15:23:48 Semprom2600-desktop kernel: [69421.926774] RPC: Registered tcp transport module.
Jun  6 15:23:48 Semprom2600-desktop kernel: [69422.033891] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Jun  6 15:24:18 Semprom2600-desktop kernel: [69452.196042] rpcbind: server localhost not responding, timed out
Jun  6 15:24:18 Semprom2600-desktop kernel: [69452.196072] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:24:48 Semprom2600-desktop kernel: [69482.196032] rpcbind: server localhost not responding, timed out
Jun  6 15:24:48 Semprom2600-desktop kernel: [69482.196062] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:25:17 Semprom2600-desktop sudo: pam_sm_authenticate: Called 
Jun  6 15:25:17 Semprom2600-desktop sudo: pam_sm_authenticate: username = [leo] 
Jun  6 15:25:17 Semprom2600-desktop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
Jun  6 15:25:18 Semprom2600-desktop kernel: [69512.196092] rpcbind: server localhost not responding, timed out
Jun  6 15:25:18 Semprom2600-desktop kernel: [69512.196119] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:25:19 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 15:25:20 Semprom2600-desktop sudo: Passphrase key already in keyring; rc = [1] 
Jun  6 15:25:20 Semprom2600-desktop sudo: There is already a key in the user session keyring for the given passphrase. 
Jun  6 15:25:48 Semprom2600-desktop kernel: [69542.196029] rpcbind: server localhost not responding, timed out
Jun  6 15:25:48 Semprom2600-desktop kernel: [69542.196059] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:26:18 Semprom2600-desktop kernel: [69572.196159] rpcbind: server localhost not responding, timed out
Jun  6 15:26:18 Semprom2600-desktop kernel: [69572.196188] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:26:18 Semprom2600-desktop kernel: [69572.196280] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jun  6 15:26:18 Semprom2600-desktop kernel: [69572.213170] NFSD: starting 90-second grace period
Jun  6 15:26:18 Semprom2600-desktop kernel: [69572.213757] nfsd: last server has exited, flushing export cache
Jun  6 15:26:48 Semprom2600-desktop kernel: [69602.212028] rpcbind: server localhost not responding, timed out
Jun  6 15:26:48 Semprom2600-desktop kernel: [69602.212058] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:27:18 Semprom2600-desktop kernel: [69632.212029] rpcbind: server localhost not responding, timed out
Jun  6 15:27:18 Semprom2600-desktop kernel: [69632.212058] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:27:48 Semprom2600-desktop kernel: [69662.212032] rpcbind: server localhost not responding, timed out
Jun  6 15:27:48 Semprom2600-desktop kernel: [69662.212061] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:28:50 Semprom2600-desktop kernel: [69723.984031] rpcbind: server localhost not responding, timed out
Jun  6 15:28:50 Semprom2600-desktop kernel: [69723.984060] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:29:20 Semprom2600-desktop kernel: [69753.984027] rpcbind: server localhost not responding, timed out
Jun  6 15:29:20 Semprom2600-desktop kernel: [69753.984055] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:29:50 Semprom2600-desktop kernel: [69783.984035] rpcbind: server localhost not responding, timed out
Jun  6 15:29:50 Semprom2600-desktop kernel: [69783.984065] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:30:20 Semprom2600-desktop kernel: [69813.984031] rpcbind: server localhost not responding, timed out
Jun  6 15:30:20 Semprom2600-desktop kernel: [69813.984059] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:30:50 Semprom2600-desktop kernel: [69843.984046] rpcbind: server localhost not responding, timed out
Jun  6 15:30:50 Semprom2600-desktop kernel: [69843.984076] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:30:50 Semprom2600-desktop kernel: [69843.984186] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jun  6 15:30:50 Semprom2600-desktop kernel: [69843.984210] NFSD: starting 90-second grace period
Jun  6 15:30:50 Semprom2600-desktop kernel: [69843.996086] nfsd: last server has exited, flushing export cache
Jun  6 15:31:20 Semprom2600-desktop kernel: [69873.996026] rpcbind: server localhost not responding, timed out
Jun  6 15:31:20 Semprom2600-desktop kernel: [69873.996055] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:31:50 Semprom2600-desktop kernel: [69903.996070] rpcbind: server localhost not responding, timed out
Jun  6 15:31:50 Semprom2600-desktop kernel: [69903.996098] RPC: failed to contact local rpcbind server (errno 5).
Jun  6 15:32:20 Semprom2600-desktop kernel: [69933.996027] rpcbind: server localhost not responding, timed out
Jun  6 15:32:20 Semprom2600-desktop kernel: [69933.996056] RPC: failed to contact local rpcbind server (errno 5).

---

### Post by leosr on 2009-06-06
Esta es la salida del archivo /var/log/dmesg
```
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x5fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  modified: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  modified: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bf000 - 37fef85b
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb185b
[    0.000000] Move RAMDISK from 00000000378bf000 - 0000000037fef85a to 00881000 - 00fb185a
[    0.000000] ACPI: RSDP 000F8EA0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 5FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5FFF3180, 61B0 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FFF0000, 0040
[    0.000000] ACPI: MCFG 5FFF9440, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 5FFF9380, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 651MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb185b]      NEW RAMDISK ==> [0000881000 - 0000fb185b]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f4fe0] 000f4fe0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0005fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005fff0
[    0.000000] On node 0 totalpages: 393087
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1304 pages used for memmap
[    0.000000]   HighMem zone: 165594 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390015
[    0.000000] Kernel command line: root=UUID=f9ecec0a-e1b5-4783-932e-cc0e15a754e0 ro quiet splash vga=789 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1608.149 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 7863680 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1535440k/1572800k available (4126k kernel code, 35952k reserved, 2208k data, 532k init, 667592k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 3216.29 BogoMIPS (lpj=6432596)
[    0.004034] Security Framework initialized
[    0.004043] SELinux:  Disabled at boot.
[    0.004071] AppArmor: AppArmor initialized
[    0.004080] Mount-cache hash table entries: 512
[    0.004224] Initializing cgroup subsys ns
[    0.004228] Initializing cgroup subsys cpuacct
[    0.004231] Initializing cgroup subsys memory
[    0.004236] Initializing cgroup subsys freezer
[    0.004250] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004253] CPU: L2 Cache: 128K (64 bytes/line)
[    0.004266] Checking 'hlt' instruction... OK.
[    0.020674] SMP alternatives: switching to UP code
[    0.162669] ACPI: Core revision 20080926
[    0.165460] ACPI: Checking initramfs for custom DSDT
[    0.515387] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.555080] CPU0: AMD Sempron(tm) Processor 2600+ stepping 00
[    0.556002] Brought up 1 CPUs
[    0.556002] Total of 1 processors activated (3216.29 BogoMIPS).
[    0.556002] CPU0 attaching NULL sched-domain.
[    0.556002] net_namespace: 776 bytes
[    0.556002] Booting paravirtualized kernel on bare hardware
[    0.556002] Time: 20:06:47  Date: 06/05/09
[    0.556002] regulator: core version 0.5
[    0.556002] NET: Registered protocol family 16
[    0.556002] EISA bus registered
[    0.556002] ACPI: bus type pci registered
[    0.556002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.556002] PCI: MCFG area at e0000000 reserved in E820
[    0.556002] PCI: Using MMCONFIG for extended config space
[    0.556002] PCI: Using configuration type 1 for base access
[    0.556002] ACPI: EC: Look up EC in DSDT
[    0.564630] ACPI: Interpreter enabled
[    0.564638] ACPI: (supports S0 S1 S4 S5)
[    0.564661] ACPI: Using IOAPIC for interrupt routing
[    0.575357] ACPI: No dock devices found.
[    0.575375] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.575471] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.575487] pci 0000:00:01.1: reg 10 io port: [0xff00-0xff1f]
[    0.575497] pci 0000:00:01.1: reg 20 io port: [0x4c00-0x4c3f]
[    0.575501] pci 0000:00:01.1: reg 24 io port: [0x4c40-0x4c7f]
[    0.575509] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.575512] pci 0000:00:01.1: PME# disabled
[    0.575531] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
[    0.575547] pci 0000:00:02.0: supports D1 D2
[    0.575549] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575552] pci 0000:00:02.0: PME# disabled
[    0.575570] pci 0000:00:02.1: reg 10 32bit mmio: [0xfeb00000-0xfeb000ff]
[    0.575586] pci 0000:00:02.1: supports D1 D2
[    0.575588] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575592] pci 0000:00:02.1: PME# disabled
[    0.575613] pci 0000:00:04.0: reg 10 io port: [0xea00-0xeaff]
[    0.575617] pci 0000:00:04.0: reg 14 io port: [0xee00-0xeeff]
[    0.575621] pci 0000:00:04.0: reg 18 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.575633] pci 0000:00:04.0: supports D1 D2
[    0.575654] pci 0000:00:06.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.575674] pci 0000:00:07.0: reg 10 io port: [0x9f0-0x9f7]
[    0.575679] pci 0000:00:07.0: reg 14 io port: [0xbf0-0xbf3]
[    0.575683] pci 0000:00:07.0: reg 18 io port: [0x970-0x977]
[    0.575687] pci 0000:00:07.0: reg 1c io port: [0xb70-0xb73]
[    0.575691] pci 0000:00:07.0: reg 20 io port: [0xf600-0xf60f]
[    0.575696] pci 0000:00:07.0: reg 24 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.575714] pci 0000:00:08.0: reg 10 io port: [0x9e0-0x9e7]
[    0.575719] pci 0000:00:08.0: reg 14 io port: [0xbe0-0xbe3]
[    0.575723] pci 0000:00:08.0: reg 18 io port: [0x960-0x967]
[    0.575727] pci 0000:00:08.0: reg 1c io port: [0xb60-0xb63]
[    0.575731] pci 0000:00:08.0: reg 20 io port: [0xf100-0xf10f]
[    0.575735] pci 0000:00:08.0: reg 24 32bit mmio: [0xfe02a000-0xfe02afff]
[    0.575764] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfe029000-0xfe029fff]
[    0.575768] pci 0000:00:0a.0: reg 14 io port: [0xf000-0xf007]
[    0.575782] pci 0000:00:0a.0: supports D1 D2
[    0.575784] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575787] pci 0000:00:0a.0: PME# disabled
[    0.575810] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575813] pci 0000:00:0b.0: PME# disabled
[    0.575835] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575838] pci 0000:00:0c.0: PME# disabled
[    0.575860] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575863] pci 0000:00:0d.0: PME# disabled
[    0.575884] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575887] pci 0000:00:0e.0: PME# disabled
[    0.575980] pci 0000:01:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.575986] pci 0000:01:00.0: reg 14 32bit mmio: [0xd8000000-0xdfffffff]
[    0.576014] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.576057] pci 0000:01:08.0: reg 20 io port: [0xdf00-0xdf1f]
[    0.576069] pci 0000:01:08.0: supports D1 D2
[    0.576071] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.576075] pci 0000:01:08.0: PME# disabled
[    0.576106] pci 0000:01:08.1: reg 20 io port: [0xde00-0xde1f]
[    0.576118] pci 0000:01:08.1: supports D1 D2
[    0.576120] pci 0000:01:08.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.576124] pci 0000:01:08.1: PME# disabled
[    0.576145] pci 0000:01:08.2: reg 10 32bit mmio: [0xfcfff000-0xfcfff0ff]
[    0.576167] pci 0000:01:08.2: supports D1 D2
[    0.576170] pci 0000:01:08.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.576173] pci 0000:01:08.2: PME# disabled
[    0.576197] pci 0000:01:09.0: reg 10 io port: [0xdd00-0xdd07]
[    0.576220] pci 0000:01:09.0: supports D2
[    0.576222] pci 0000:01:09.0: PME# supported from D0 D2 D3hot D3cold
[    0.576226] pci 0000:01:09.0: PME# disabled
[    0.576248] pci 0000:00:09.0: transparent bridge
[    0.576251] pci 0000:00:09.0: bridge io port: [0xd000-0xdfff]
[    0.576255] pci 0000:00:09.0: bridge 32bit mmio: [0xfb000000-0xfcffffff]
[    0.576259] pci 0000:00:09.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.576291] pci 0000:00:0b.0: bridge io port: [0xc000-0xcfff]
[    0.576295] pci 0000:00:0b.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.576299] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.576331] pci 0000:00:0c.0: bridge io port: [0xb000-0xbfff]
[    0.576335] pci 0000:00:0c.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.576339] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.576371] pci 0000:00:0d.0: bridge io port: [0xa000-0xafff]
[    0.576374] pci 0000:00:0d.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.576379] pci 0000:00:0d.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.576410] pci 0000:00:0e.0: bridge io port: [0x9000-0x9fff]
[    0.576414] pci 0000:00:0e.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    0.576418] pci 0000:00:0e.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.576428] bus 00 -> node 0
[    0.576438] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.576926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.654977] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.655225] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.655472] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.655718] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.655962] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.656220] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.656464] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.656711] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.656957] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.657202] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.657459] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.657704] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.657958] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.658215] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.658474] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.658731] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.659002] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.659272] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.659536] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.659799] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.659975] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.660261] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.660534] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.660806] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.661078] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[    0.661350] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0
[    0.661622] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.661894] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.662166] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.662449] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.662731] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.663012] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.663189] ACPI: WMI: Mapper loaded
[    0.663401] SCSI subsystem initialized
[    0.663447] libata version 3.00 loaded.
[    0.663496] usbcore: registered new interface driver usbfs
[    0.663514] usbcore: registered new interface driver hub
[    0.663541] usbcore: registered new device driver usb
[    0.663655] PCI: Using ACPI for IRQ routing
[    0.663758] Bluetooth: Core ver 2.13
[    0.663758] NET: Registered protocol family 31
[    0.663758] Bluetooth: HCI device and connection manager initialized
[    0.663758] Bluetooth: HCI socket layer initialized
[    0.663758] NET: Registered protocol family 8
[    0.663758] NET: Registered protocol family 20
[    0.663758] NetLabel: Initializing
[    0.663758] NetLabel:  domain hash size = 128
[    0.663758] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.663758] NetLabel:  unlabeled traffic allowed by default
[    0.663758] AppArmor: AppArmor Filesystem Enabled
[    0.663758] pnp: PnP ACPI init
[    0.663758] ACPI: bus type pnp registered
[    0.671152] pnp: PnP ACPI: found 14 devices
[    0.671156] ACPI: ACPI bus type pnp unregistered
[    0.671160] PnPBIOS: Disabled by ACPI PNP
[    0.671172] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.671176] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.671179] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.671182] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.671185] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.671189] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.671196] system 00:02: ioport range 0xb78-0xb7b has been reserved
[    0.671199] system 00:02: ioport range 0xf78-0xf7b has been reserved
[    0.671202] system 00:02: ioport range 0xa78-0xa7b has been reserved
[    0.671205] system 00:02: ioport range 0xe78-0xe7b has been reserved
[    0.671209] system 00:02: ioport range 0xbbc-0xbbf has been reserved
[    0.671216] system 00:02: ioport range 0xfbc-0xfbf has been reserved
[    0.671219] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.671223] system 00:02: ioport range 0x290-0x30f has been reserved
[    0.671233] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.671240] system 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[    0.671243] system 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[    0.671246] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.671249] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.671253] system 00:0d: iomem range 0x5fff0000-0x5fffffff could not be reserved
[    0.671256] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.671260] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.671263] system 00:0d: iomem range 0x100000-0x5ffeffff could not be reserved
[    0.671266] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.671270] system 00:0d: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.671273] system 00:0d: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.671277] system 00:0d: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.671280] system 00:0d: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.671283] system 00:0d: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.706018] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    0.706022] pci 0000:00:09.0:   IO window: 0xd000-0xdfff
[    0.706026] pci 0000:00:09.0:   MEM window: 0xfb000000-0xfcffffff
[    0.706029] pci 0000:00:09.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
[    0.706034] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.706036] pci 0000:00:0b.0:   IO window: 0xc000-0xcfff
[    0.706040] pci 0000:00:0b.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.706043] pci 0000:00:0b.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.706048] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.706050] pci 0000:00:0c.0:   IO window: 0xb000-0xbfff
[    0.706054] pci 0000:00:0c.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.706057] pci 0000:00:0c.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.706061] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.706064] pci 0000:00:0d.0:   IO window: 0xa000-0xafff
[    0.706068] pci 0000:00:0d.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.706071] pci 0000:00:0d.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.706075] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05
[    0.706078] pci 0000:00:0e.0:   IO window: 0x9000-0x9fff
[    0.706081] pci 0000:00:0e.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.706085] pci 0000:00:0e.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.706094] pci 0000:00:09.0: setting latency timer to 64
[    0.706099] pci 0000:00:0b.0: setting latency timer to 64
[    0.706105] pci 0000:00:0c.0: setting latency timer to 64
[    0.706110] pci 0000:00:0d.0: setting latency timer to 64
[    0.706115] pci 0000:00:0e.0: setting latency timer to 64
[    0.706118] bus: 00 index 0 io port: [0x00-0xffff]
[    0.706121] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.706123] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.706126] bus: 01 index 1 mmio: [0xfb000000-0xfcffffff]
[    0.706129] bus: 01 index 2 mmio: [0xd8000000-0xdfffffff]
[    0.706131] bus: 01 index 3 io port: [0x00-0xffff]
[    0.706133] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.706136] bus: 02 index 0 io port: [0xc000-0xcfff]
[    0.706138] bus: 02 index 1 mmio: [0xfdf00000-0xfdffffff]
[    0.706141] bus: 02 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.706143] bus: 02 index 3 mmio: [0x0-0x0]
[    0.706146] bus: 03 index 0 io port: [0xb000-0xbfff]
[    0.706148] bus: 03 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.706150] bus: 03 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.706153] bus: 03 index 3 mmio: [0x0-0x0]
[    0.706155] bus: 04 index 0 io port: [0xa000-0xafff]
[    0.706157] bus: 04 index 1 mmio: [0xfdb00000-0xfdbfffff]
[    0.706160] bus: 04 index 2 mmio: [0xfda00000-0xfdafffff]
[    0.706162] bus: 04 index 3 mmio: [0x0-0x0]
[    0.706164] bus: 05 index 0 io port: [0x9000-0x9fff]
[    0.706167] bus: 05 index 1 mmio: [0xfd900000-0xfd9fffff]
[    0.706169] bus: 05 index 2 mmio: [0xfd800000-0xfd8fffff]
[    0.706172] bus: 05 index 3 mmio: [0x0-0x0]
[    0.706187] NET: Registered protocol family 2
[    0.706229] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.706229] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.706229] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.708030] Switched to high resolution mode on CPU 0
[    0.708272] TCP: Hash tables configured (established 131072 bind 65536)
[    0.708276] TCP reno registered
[    0.708423] NET: Registered protocol family 1
[    0.708561] checking if image is initramfs... it is
[    1.429770] Freeing initrd memory: 7362k freed
[    1.429875] cpufreq: No nForce2 chipset.
[    1.430025] audit: initializing netlink socket (disabled)
[    1.430042] type=2000 audit(1244232407.428:1): initialized
[    1.439682] highmem bounce pool size: 64 pages
[    1.439688] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.441133] VFS: Disk quotas dquot_6.5.1
[    1.441202] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.441896] fuse init (API version 7.10)
[    1.441989] msgmni has been set to 1711
[    1.442194] alg: No test for stdrng (krng)
[    1.442208] io scheduler noop registered
[    1.442210] io scheduler anticipatory registered
[    1.442212] io scheduler deadline registered
[    1.442235] io scheduler cfq registered (default)
[    1.442257] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.456084] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.456093] pci 0000:00:0b.0: Found enabled HT MSI Mapping
[    1.456098] pci 0000:00:0b.0: Linking AER extended capability
[    1.456108] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.456115] pci 0000:00:0c.0: Found enabled HT MSI Mapping
[    1.456118] pci 0000:00:0c.0: Linking AER extended capability
[    1.456127] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.456134] pci 0000:00:0d.0: Found enabled HT MSI Mapping
[    1.456137] pci 0000:00:0d.0: Linking AER extended capability
[    1.456147] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.456154] pci 0000:00:0e.0: Found enabled HT MSI Mapping
[    1.456157] pci 0000:00:0e.0: Linking AER extended capability
[    1.456174] pci 0000:01:00.0: Boot video device
[    1.463796] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.463818] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.463835] pcieport-driver 0000:00:0b.0: irq 2303 for MSI/MSI-X
[    1.463841] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.463860] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.463899] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.463919] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.463931] pcieport-driver 0000:00:0c.0: irq 2302 for MSI/MSI-X
[    1.463937] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.463950] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.463985] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.464025] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.464036] pcieport-driver 0000:00:0d.0: irq 2301 for MSI/MSI-X
[    1.464043] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.464059] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.464095] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.464114] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.464125] pcieport-driver 0000:00:0e.0: irq 2300 for MSI/MSI-X
[    1.464131] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.464145] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.464191] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.464201] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.464352] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.464355] ACPI: Power Button (FF) [PWRF]
[    1.464403] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.464405] ACPI: Power Button (CM) [PWRB]
[    1.464463] fan PNP0C0B:00: registered as cooling_device0
[    1.464469] ACPI: Fan [FAN] (on)
[    1.465119] processor ACPI_CPU:00: registered as cooling_device1
[    1.470077] thermal LNXTHERM:01: registered as thermal_zone0
[    1.470188] ACPI: Thermal Zone [THRM] (22 C)
[    1.470242] isapnp: Scanning for PnP cards...
[    1.822714] isapnp: No Plug & Play device found
[    1.824068] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.824154] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.824237] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.824520] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.824635] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.825086] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.825098] serial 0000:01:09.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.825165] 0000:01:09.0: ttyS2 at I/O 0xdd00 (irq = 19) is a 16550A
[    1.825901] brd: module loaded
[    1.826259] loop: module loaded
[    1.826356] Fixed MDIO Bus: probed
[    1.826364] PPP generic driver version 2.4.2
[    1.826435] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.826473] Driver 'sd' needs updating - please use bus_type methods
[    1.826482] Driver 'sr' needs updating - please use bus_type methods
[    1.826683] sata_nv 0000:00:07.0: version 3.5
[    1.827222] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.827233] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.827296] sata_nv 0000:00:07.0: setting latency timer to 64
[    1.827397] scsi0 : sata_nv
[    1.827507] scsi1 : sata_nv
[    1.827730] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf600 irq 23
[    1.827733] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf608 irq 23
[    2.704030] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.712273] ata1.00: ATA-7: HDS728080PLA380, PF2OA69A, max UDMA/133
[    2.712277] ata1.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.728282] ata1.00: configured for UDMA/133
[    3.608027] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.616116] ata2.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL01, max UDMA/100
[    3.632136] ata2.00: configured for UDMA/100
[    3.739619] scsi 0:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
[    3.739737] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)
[    3.739754] sd 0:0:0:0: [sda] Write Protect is off
[    3.739757] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.739783] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.739852] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)
[    3.739867] sd 0:0:0:0: [sda] Write Protect is off
[    3.739870] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.739894] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.739899]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    3.789163] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.789218] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.792156] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL01 PQ: 0 ANSI: 5
[    4.123051] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.123056] Uniform CD-ROM driver Revision: 3.20
[    4.123176] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.123236] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.123786] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    4.123797] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    4.123854] sata_nv 0000:00:08.0: setting latency timer to 64
[    4.123938] scsi2 : sata_nv
[    4.124039] scsi3 : sata_nv
[    4.124251] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf100 irq 22
[    4.124254] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf108 irq 22
[    4.848024] ata3: SATA link down (SStatus 0 SControl 300)
[    5.572022] ata4: SATA link down (SStatus 0 SControl 300)
[    5.572134] pata_amd 0000:00:06.0: version 0.3.10
[    5.572181] pata_amd 0000:00:06.0: setting latency timer to 64
[    5.572265] scsi4 : pata_amd
[    5.572333] scsi5 : pata_amd
[    5.573136] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfb00 irq 14
[    5.573139] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfb08 irq 15
[    5.736263] ata5.00: ATAPI: LITE-ON CD-RW SOHR-5238S, 4S09, max UDMA/33
[    5.736292] ata5: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:120:0x1b)
[    5.752212] ata5.00: configured for UDMA/33
[    5.919625] scsi 4:0:0:0: CD-ROM            LITE-ON  CD-RW SOHR-5238S 4S09 PQ: 0 ANSI: 5
[    5.924604] sr1: scsi3-mmc drive: 40x/52x writer cd/rw xa/form2 cdda tray
[    5.924696] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    5.924754] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    5.925275] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.925727] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    5.925739] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    5.925761] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    5.925765] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    5.925837] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    5.925867] ehci_hcd 0000:00:02.1: debug port 1
[    5.925871] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    5.925889] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
[    5.936034] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    5.936122] usb usb1: configuration #1 chosen from 1 choice
[    5.936155] hub 1-0:1.0: USB hub found
[    5.936172] hub 1-0:1.0: 10 ports detected
[    5.936605] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    5.936616] ehci_hcd 0000:01:08.2: PCI INT C -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    5.936638] ehci_hcd 0000:01:08.2: setting latency timer to 64
[    5.936642] ehci_hcd 0000:01:08.2: EHCI Host Controller
[    5.936703] ehci_hcd 0000:01:08.2: new USB bus registered, assigned bus number 2
[    5.936751] ehci_hcd 0000:01:08.2: irq 16, io mem 0xfcfff000
[    5.948035] ehci_hcd 0000:01:08.2: USB 2.0 started, EHCI 1.00
[    5.948113] usb usb2: configuration #1 chosen from 1 choice
[    5.948142] hub 2-0:1.0: USB hub found
[    5.948152] hub 2-0:1.0: 4 ports detected
[    5.948256] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.948703] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    5.948714] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    5.948734] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    5.948738] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    5.948800] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    5.948829] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    6.006084] usb usb3: configuration #1 chosen from 1 choice
[    6.006120] hub 3-0:1.0: USB hub found
[    6.006131] hub 3-0:1.0: 10 ports detected
[    6.006239] uhci_hcd: USB Universal Host Controller Interface driver
[    6.006598] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    6.006609] uhci_hcd 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    6.006619] uhci_hcd 0000:01:08.0: setting latency timer to 64
[    6.006622] uhci_hcd 0000:01:08.0: UHCI Host Controller
[    6.006690] uhci_hcd 0000:01:08.0: new USB bus registered, assigned bus number 4
[    6.006722] uhci_hcd 0000:01:08.0: irq 18, io base 0x0000df00
[    6.006815] usb usb4: configuration #1 chosen from 1 choice
[    6.006843] hub 4-0:1.0: USB hub found
[    6.006852] hub 4-0:1.0: 2 ports detected
[    6.006949] uhci_hcd 0000:01:08.1: PCI INT B -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    6.006955] uhci_hcd 0000:01:08.1: setting latency timer to 64
[    6.006959] uhci_hcd 0000:01:08.1: UHCI Host Controller
[    6.007007] uhci_hcd 0000:01:08.1: new USB bus registered, assigned bus number 5
[    6.007034] uhci_hcd 0000:01:08.1: irq 19, io base 0x0000de00
[    6.007115] usb usb5: configuration #1 chosen from 1 choice
[    6.007141] hub 5-0:1.0: USB hub found
[    6.007148] hub 5-0:1.0: 2 ports detected
[    6.007274] usbcore: registered new interface driver libusual
[    6.007310] usbcore: registered new interface driver usbserial
[    6.007321] USB Serial support registered for generic
[    6.007337] usbcore: registered new interface driver usbserial_generic
[    6.007339] usbserial: USB Serial Driver core
[    6.007384] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    6.007387] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    6.007729] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.007867] mice: PS/2 mouse device common for all mice
[    6.008057] rtc_cmos 00:04: RTC can wake from S4
[    6.008093] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    6.008117] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    6.008203] device-mapper: uevent: version 1.0.3
[    6.008328] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    6.008379] device-mapper: multipath: version 1.0.5 loaded
[    6.008382] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.008480] EISA: Probing bus 0 at eisa.0
[    6.008495] Cannot allocate resource for EISA slot 4
[    6.008507] EISA: Detected 0 cards.
[    6.008538] cpuidle: using governor ladder
[    6.008540] cpuidle: using governor menu
[    6.009123] TCP cubic registered
[    6.009233] NET: Registered protocol family 10
[    6.009681] lo: Disabled Privacy Extensions
[    6.010026] NET: Registered protocol family 17
[    6.010048] Bluetooth: L2CAP ver 2.11
[    6.010050] Bluetooth: L2CAP socket layer initialized
[    6.010053] Bluetooth: SCO (Voice Link) ver 0.6
[    6.010055] Bluetooth: SCO socket layer initialized
[    6.010113] Bluetooth: RFCOMM socket layer initialized
[    6.010122] Bluetooth: RFCOMM TTY layer initialized
[    6.010124] Bluetooth: RFCOMM ver 1.10
[    6.010157] powernow-k8: Power state transitions not supported
[    6.010179] Using IPI No-Shortcut mode
[    6.010278] registered taskstats version 1
[    6.010436]   Magic number: 13:560:143
[    6.010458] block ram8: hash matches
[    6.010498] acpi device:14: hash matches
[    6.010534] rtc_cmos 00:04: setting system clock to 2009-06-05 20:06:52 UTC (1244232412)
[    6.010537] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.010539] EDD information not available.
[    6.011062] Freeing unused kernel memory: 532k freed
[    6.011218] Write protecting the kernel text: 4128k
[    6.011270] Write protecting the kernel read-only data: 1532k
[    6.056983] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    6.105695] vesafb: framebuffer at 0xd8000000, mapped to 0xf7d00000, using 3750k, total 131072k
[    6.105701] vesafb: mode is 800x600x32, linelength=3200, pages=1
[    6.105704] vesafb: protected mode interface info at c000:f090
[    6.105708] vesafb: pmi: set display start = c00cf0c6, set palette = c00cf130
[    6.105710] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    6.105723] vesafb: scrolling: redraw
[    6.105726] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    6.105820] Console: switching to colour frame buffer device 100x37
[    6.163888] fb0: VESA VGA frame buffer device
[    6.288027] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    6.515136] Floppy drive(s): fd0 is 1.44M
[    6.536118] FDC 0 is a post-1991 82077
[    6.599000] usb 1-1: configuration #1 chosen from 1 choice
[    6.629601] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    6.630051] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    6.630057] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    6.630063] forcedeth 0000:00:0a.0: setting latency timer to 64
[    6.630146] nv_probe: set workaround bit for reversed mac addr
[    6.712222] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    6.845873] usb 1-2: configuration #1 chosen from 1 choice
[    6.956027] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    7.094756] usb 1-7: configuration #1 chosen from 1 choice
[    7.148864] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:13:d3:a4:1a:7c
[    7.148869] forcedeth 0000:00:0a.0: highdma csum timirq gbit lnktim desc-v3
[    7.264046] hub 1-0:1.0: over-current change on port 3
[    7.357727] PM: Starting manual resume from disk
[    7.357732] PM: Resume from partition 8:7
[    7.357735] PM: Checking hibernation image.
[    7.357911] PM: Resume from disk failed.
[    7.368034] hub 1-0:1.0: over-current change on port 4
[    7.380451] EXT4-fs: barriers enabled
[    7.409513] kjournald2 starting.  Commit interval 5 seconds
[    7.409530] EXT4-fs: delayed allocation enabled
[    7.409532] EXT4-fs: file extents enabled
[    7.410790] EXT4-fs: mballoc enabled
[    7.410796] EXT4-fs: mounted filesystem with ordered data mode.
[    7.776213] usb 3-8: new low speed USB device using ohci_hcd and address 2
[    7.989152] usb 3-8: configuration #1 chosen from 1 choice
[    8.232037] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    8.397143] usb 4-1: configuration #1 chosen from 1 choice
[    8.400081] hub 4-1:1.0: USB hub found
[    8.402051] hub 4-1:1.0: 4 ports detected
[    8.685095] usb 4-1.1: new full speed USB device using uhci_hcd and address 3
[    8.935218] usb 4-1.1: configuration #1 chosen from 1 choice
[   11.236505] udev: starting version 141
[   11.367667] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   11.367714] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   11.400923] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.400968] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.460802] usbcore: registered new interface driver hiddev
[   11.467584] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.0/usb3/3-8/3-8:1.0/input/input4
[   11.485952] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10C4
[   11.488084] usblp1: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B6
[   11.488115] usbcore: registered new interface driver usblp
[   11.500295] generic-usb 0003:045E:0047.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-8/input0
[   11.500322] usbcore: registered new interface driver usbhid
[   11.500349] usbhid: v2.6:USB HID core driver
[   11.776979] Linux agpgart interface v0.103
[   11.994474] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   11.994604] usbcore: registered new interface driver btusb
[   12.161181] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.364868] nvidia: module license 'NVIDIA' taints kernel.
[   12.638361] nvidia 0000:01:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   12.638370] nvidia 0000:01:00.0: setting latency timer to 64
[   12.640238] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.16  Sat Jan 24 19:42:59 PST 2009
[   12.655805] ppdev: user-space parallel port driver
[   12.768330] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   12.768338] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   12.768412] Intel ICH 0000:00:04.0: setting latency timer to 64
[   13.092028] intel8x0_measure_ac97_clock: measured 54794 usecs
[   13.092032] intel8x0: clocking to 46966
[   13.234809] lp0: using parport0 (interrupt-driven).
[   13.419239] Adding 522072k swap on /dev/sda7.  Priority:-1 extents:1 across:522072k
[   13.973730] EXT4 FS on sda5, internal journal on sda5:8
[   21.785875] EXT4-fs: barriers enabled
[   21.802570] kjournald2 starting.  Commit interval 5 seconds
[   21.802834] EXT4 FS on sda6, internal journal on sda6:8
[   21.802837] EXT4-fs: delayed allocation enabled
[   21.802839] EXT4-fs: file extents enabled
[   21.803883] EXT4-fs: mballoc enabled
[   21.803889] EXT4-fs: mounted filesystem with ordered data mode.
[   22.117107] type=1505 audit(1244243228.605:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2193
[   22.187351] type=1505 audit(1244243228.673:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2197
[   22.187544] type=1505 audit(1244243228.673:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2197
[   22.187614] type=1505 audit(1244243228.673:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2197
[   22.187668] type=1505 audit(1244243228.673:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2197
[   22.234285] type=1505 audit(1244243228.721:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2202
[   22.276487] type=1505 audit(1244243228.765:8): operation="profile_load" name="/usr/sbin/clamd" name2="default" pid=2206
[   22.468386] type=1505 audit(1244243228.957:9): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2210
[   22.468652] type=1505 audit(1244243228.957:10): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2210
[   22.523241] type=1505 audit(1244243229.009:11): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2214
[   30.776032] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   30.776037] vboxdrv: Successfully done.
[   30.776039] vboxdrv: Found 1 processor cores.
[   30.776143] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   30.776146] vboxdrv: Successfully loaded version 2.2.4 (interface 0x000a0009).
[   32.695456] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.695460] Bluetooth: BNEP filters: protocol multicast
[   32.720738] Bridge firewalling registered
```

---

### Post by guillermolisi on 2009-06-06
Esos logs son de una misma maquina ?
De cual de las dos ?

La maquina que usa EXT4 es el server ?

Voy a buscar si hay alguna incompatibilidad para NFS  con EXT4.

Por las dudas, probe "RPC: failed to contact local rpcbind server (errno 5)" en Google" y salio mucha informacion, por lo menos en Ingles.

---

### Post by leosr on 2009-06-06
> **guillermolisi said:**
> Esos logs son de una misma maquina ?
De cual de las dos ?

La maquina que usa EXT4 es el server ?

Voy a buscar si hay alguna incompatibilidad para NFS  con EXT4.

Por las dudas, probe "RPC: failed to contact local rpcbind server (errno 5)" en Google" y salio mucha informacion, por lo menos en Ingles.

Las 2 máquinas están formateadas con ext4. El log es de la que va a ser Server. En la otra funciona bien nfs, por lo menos lo instalé sin problemas (tiene Xubuntu Jaunty).
Mis conocimientos de redes son limitados... más en Linux.

---

### Post by leosr on 2009-06-06
Podrá tener algo que ver la configuración del router?

---

### Post by guillermolisi on 2009-06-07
Fijate en el contenido del archivo /etc/network/interfaces si tenes las siguientes lineas: ```
# The loopback network interface
auto lo
iface lo inet loopback
```

si no las tenes, agregalas y volve a probar.

Si no funciona volve a mostrar el contenido de los dos logs que enviaste para ver si hubo algun cambio en RPC, que esta dando un error que no deberia.

---

### Post by leosr on 2009-06-09
> **guillermolisi said:**
> Fijate en el contenido del archivo /etc/network/interfaces si tenes las siguientes lineas: ```
# The loopback network interface
auto lo
iface lo inet loopback
```

si no las tenes, agregalas y volve a probar.

Si no funciona volve a mostrar el contenido de los dos logs que enviaste para ver si hubo algun cambio en RPC, que esta dando un error que no deberia.
Están esas líneas en el archivo.

Hoy al encender la máquina bajé unas actualizaciones y al final me tiró el error: E: Sub-process /usr/bin/dpkg returned an error code (1)
No pude encontrar ninguna solución, por lo que veo NFS no se puede terminar de instalar, por eso no funciona.
Adjunto un pantallazo del error que tiró.

---

### Post by guillermolisi on 2009-06-09
> **leosr said:**
> Están esas líneas en el archivo.

Hoy al encender la máquina bajé unas actualizaciones y al final me tiró el error: E: Sub-process /usr/bin/dpkg returned an error code (1)
No pude encontrar ninguna solución, por lo que veo NFS no se puede terminar de instalar, por eso no funciona.
Adjunto un pantallazo del error que tiró.

Problemas de dependencias ? Mmmmmm .....

Las demas actualizaciones bajaron bien, sin errores ?

Habra posibilidad de ver el mensaje de error completo para encontrar el por que de esta falta de resolucion de dependencias ? (volviendo a intentar pero con apt-get por ejemplo, en consola).

---

### Post by leosr on 2009-06-10
> **guillermolisi said:**
> Problemas de dependencias ? Mmmmmm .....

Las demas actualizaciones bajaron bien, sin errores ?

Habra posibilidad de ver el mensaje de error completo para encontrar el por que de esta falta de resolucion de dependencias ? (volviendo a intentar pero con apt-get por ejemplo, en consola).

Cualquier cosa que quiero instalar se instala sin problemas. Sólo me tira el error de NFS. Incluso pasa desde la consola. 
Dónde está el archivo del log así lo posteo?

---

### Post by guillermolisi on 2009-06-10
> **leosr said:**
> Cualquier cosa que quiero instalar se instala sin problemas. Sólo me tira el error de NFS. Incluso pasa desde la consola. 
Dónde está el archivo del log así lo posteo?
Si usas apt-get podes copiar y pegar lo que ves en la terminal/consola.

---

### Post by leosr on 2009-06-10
acá va lo que sale en la consola:
```
leo@Semprom2600-desktop:~$ sudo apt-get install nfs-common nfs-kernel-server
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  nfs-common nfs-kernel-server
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 350kB de archivos.
Se utilizarán 946kB de espacio de disco adicional después de esta operación.
Des:1 http://ar.archive.ubuntu.com jaunty/main nfs-common 1:1.1.4-1ubuntu1 [198kB]
Des:2 http://ar.archive.ubuntu.com jaunty/main nfs-kernel-server 1:1.1.4-1ubuntu1 [152kB]
Descargados 350kB en 6s (56,5kB/s)                                             
Seleccionando el paquete nfs-common previamente no seleccionado.
(Leyendo la base de datos ...  
220125 ficheros y directorios instalados actualmente.)
Desempaquetando nfs-common (de .../nfs-common_1%3a1.1.4-1ubuntu1_i386.deb) ...
Seleccionando el paquete nfs-kernel-server previamente no seleccionado.
Desempaquetando nfs-kernel-server (de .../nfs-kernel-server_1%3a1.1.4-1ubuntu1_i386.deb) ...
Procesando disparadores para man-db ...
Configurando nfs-common (1:1.1.4-1ubuntu1) ...
 * Starting NFS common utilities                                         [fail] 
invoke-rc.d: initscript nfs-common, action "start" failed.
dpkg: error al procesar nfs-common (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de nfs-kernel-server:
 nfs-kernel-server depende de nfs-common (>= 1:1.0.8-1); sin embargo:
 El paquete `nfs-common' no está configurado todavía.
dpkg: error al procesar nfs-kernel-server (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                             Se encontraron errores al procesar:
 nfs-common
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
leo@Semprom2600-desktop:~$ 

```

---

### Post by guillermolisi on 2009-06-10
> **leosr said:**
> acá va lo que sale en la consola:
```
Configurando nfs-common (1:1.1.4-1ubuntu1) ...
 * Starting NFS common utilities                                         [fail] 
invoke-rc.d: initscript nfs-common, action "start" failed.
dpkg: error al procesar nfs-common (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de nfs-kernel-server:
 nfs-kernel-server depende de nfs-common (>= 1:1.0.8-1); sin embargo:
 El paquete `nfs-common' no está configurado todavía.

```
Ahi hay algo que no esta bien, en la ejecucion del archivo de inicio del NFS-Common.

El script /usr/sbin/invoke-rc.d esta queriendo iniciar el servicio de nfs-common y por alguna razon (parametros que falta o sobran, tal vez) da error.

Como nfs-common es una dependencia necesaria para nfs-kernel-server y no se inicio, entonces cancela toda la instalacion y puesta en marcha.

Es decir, las dependencias a nivel paquetes estan bien resueltas, lo que esta mal es que los servicios de base no se inician y los servicios siguientes tampoco a raiz de lo primero.

La verdad, rarisimo este error.

Cual es el contenido de tu /usr/sbin/invoke-rc.d ?

---

### Post by leosr on 2009-06-10
> **guillermolisi said:**
> Ahi hay algo que no esta bien, en la ejecucion del archivo de inicio del NFS-Common.

El script /usr/sbin/invoke-rc.d esta queriendo iniciar el servicio de nfs-common y por alguna razon (parametros que falta o sobran, tal vez) da error.

Como nfs-common es una dependencia necesaria para nfs-kernel-server y no se inicio, entonces cancela toda la instalacion y puesta en marcha.

Es decir, las dependencias a nivel paquetes estan bien resueltas, lo que esta mal es que los servicios de base no se inician y los servicios siguientes tampoco a raiz de lo primero.

La verdad, rarisimo este error.

Cual es el contenido de tu /usr/sbin/invoke-rc.d ?

Acá vá el contenido de /usr/sbin/invoke-rc.d

```
#!/bin/sh  
#
# invoke-rc.d.sysvinit - Executes initscript actions
#
# SysVinit /etc/rc?.d version for Debian's sysvinit package
#
# Copyright (C) 2000,2001 Henrique de Moraes Holschuh <hmh@debian.org>
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the Free
# Software Foundation; either version 2 of the License, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
# for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA.

# Constants
RUNLEVEL=/sbin/runlevel
POLICYHELPER=/usr/sbin/policy-rc.d
INITDPREFIX=/etc/init.d/
RCDPREFIX=/etc/rc

# Options
BEQUIET=
MODE=
ACTION=
FALLBACK=
NOFALLBACK=
FORCE=
RETRY=
RETURNFAILURE=
RC=

# Shell options
set +e

dohelp () {
 # 
 # outputs help and usage
 #
cat <<EOF

invoke-rc.d, Debian/SysVinit (/etc/rc?.d) initscript subsystem.
Copyright (c) 2000,2001 Henrique de Moraes Holschuh <hmh@debian.org>

Usage:
  invoke-rc.d [options] <basename> <action> [extra parameters]

  basename - Initscript ID, as per update-rc.d(8)
  action   - Initscript action. Known actions are:
                start, [force-]stop, restart,
                [force-]reload, status
  WARNING: not all initscripts implement all of the above actions.

  extra parameters are passed as is to the initscript, following 
  the action (first initscript parameter).

Options:
  --quiet
     Quiet mode, no error messages are generated.
  --force
     Try to run the initscript regardless of policy and subsystem
     non-fatal errors.
  --try-anyway
     Try to run init script even if a non-fatal error is found.
  --disclose-deny
     Return status code 101 instead of status code 0 if
     initscript action is denied by local policy rules or
     runlevel constrains.
  --query
     Returns one of status codes 100-106, does not run
     the initscript. Implies --disclose-deny and --no-fallback.
  --no-fallback
     Ignores any fallback action requests by the policy layer.
     Warning: this is usually a very *bad* idea for any actions
     other than "start".
  --help
     Outputs help message to stdout

EOF
}

printerror () {
 #
 # prints an error message
 #  $* - error message
 #
if test x${BEQUIET} = x ; then
    echo `basename $0`: "$*" >&2
fi
}

formataction () {
 #
 # formats a list in $* into $printaction
 # for human-friendly printing to stderr
 # and sets $naction to action or actions
 #
printaction=`echo $* | sed 's/ /, /g'`
if test $# -eq 1 ; then
    naction=action
else
    naction=actions
fi
}

querypolicy () {
 #
 # queries policy database
 # returns: $RC = 104 - ok, run
 #          $RC = 101 - ok, do not run
 #        other - exit with status $RC, maybe run if $RETRY
 #          initial status of $RC is taken into account.
 #

policyaction="${ACTION}"
if test x${RC} = "x101" ; then
    if test "${ACTION}" = "start" || test "${ACTION}" = "restart" ; then
	policyaction="(${ACTION})"
    fi
fi

if test "x${POLICYHELPER}" != x && test -x "${POLICYHELPER}" ; then
    FALLBACK=`${POLICYHELPER} ${BEQUIET} ${INITSCRIPTID} "${policyaction}" ${RL}`
    RC=$?
    formataction ${ACTION}
    case ${RC} in
	0)   RC=104
	     ;;
	1)   RC=105
	     ;;
	101) if test x${FORCE} != x ; then
		printerror Overriding policy-rc.d denied execution of ${printaction}.
		RC=104
	     fi
	     ;;
    esac
    if test x${MODE} != xquery ; then
      case ${RC} in
	105) printerror policy-rc.d query returned \"behaviour undefined\",
	     printerror assuming \"${printaction}\" is allowed.
	     RC=104
	     ;;
	106) formataction ${FALLBACK}
	     if test x${FORCE} = x ; then
		 if test x${NOFALLBACK} = x ; then
		     ACTION="${FALLBACK}"
		     printerror executing ${naction} \"${printaction}\" instead due to policy-rc.d request.
		     RC=104
		 else
		     printerror ignoring policy-rc.d fallback request: ${printaction}.
		     RC=101
		 fi
	     else
		 printerror ignoring policy-rc.d fallback request: ${printaction}.
		 RC=104
	     fi
	     ;;
      esac
    fi
    case ${RC} in
      100|101|102|103|104|105|106) ;;
      *) printerror WARNING: policy-rc.d returned unexpected error status ${RC}, 102 used instead.
         RC=102
	 ;;
    esac
else
    if test x${RC} = x ; then 
	RC=104
    fi
fi
return
}

verifyparameter () {
 #
 # Verifies if $1 is not null, and $# = 1
 #
if test $# -eq 0 ; then
    printerror syntax error: invalid empty parameter
    exit 103
elif test $# -ne 1 ; then
    printerror syntax error: embedded blanks are not allowed in \"$*\"
    exit 103
fi
return
}

##
##  main
##

## Verifies command line arguments

if test $# -eq 0 ; then
  printerror syntax error: missing required parameter, --help assumed
  dohelp
  exit 103
fi

state=I
while test $# -gt 0 && test ${state} != III ; do
    case "$1" in
      --help)   dohelp 
		exit 0
		;;
      --quiet)  BEQUIET=--quiet
		;;
      --force)  FORCE=yes
		RETRY=yes
		;;
      --try-anyway)
	        RETRY=yes
		;;
      --disclose-deny)
		RETURNFAILURE=yes
		;;
      --query)  MODE=query
		RETURNFAILURE=yes
		;;
      --no-fallback)
		NOFALLBACK=yes
		;;
      --*)	printerror syntax error: unknown option \"$1\"
		exit 103
		;;
	*)      case ${state} in
		I)  verifyparameter $1
		    INITSCRIPTID=$1
		    ;;
		II) verifyparameter $1
		    ACTION=$1
		    ;;
		esac
		state=${state}I
		;;
    esac
    shift
done

if test ${state} != III ; then
    printerror syntax error: missing required parameter
    exit 103
fi

#NOTE: It may not be obvious, but "$@" from this point on must expand
#to the extra initscript parameters, except inside functions.

## sanity checks and just-in-case warnings.
case ${ACTION} in
    start|stop|force-stop|restart|reload|force-reload|status)
	;;
    *)
	if test "x${POLICYHELPER}" != x && test -x "${POLICYHELPER}" ; then
	    printerror action ${ACTION} is unknown, but proceeding anyway.
	fi
	;;
esac

## Verifies if the given initscript ID is known
## For sysvinit, this error is critical
if test ! -f "${INITDPREFIX}${INITSCRIPTID}" ; then
    printerror unknown initscript, ${INITDPREFIX}${INITSCRIPTID} not found.
    exit 100
fi

## Queries sysvinit for the current runlevel
RL=`${RUNLEVEL} | sed 's/.*\ //'`
if test ! $? ; then
    printerror "could not determine current runlevel"
    if test x${RETRY} = x ; then
	exit 102
    fi
    RL=
fi

## Running ${RUNLEVEL} to get current runlevel do not work in the boot
## runlevel (scripts in /etc/rcS.d/), as /var/run/utmp contain
## runlevel 0 or 6 (written at shutdown) at that point.
if test x${RL} = x0 || test x${RL} = x6 ; then
    if ps -fp 1 | grep -q 'init boot' ; then
       RL=S
    fi
fi

## Handles shutdown sequences VERY safely
## i.e.: forget about policy, and do all we can to run the script.
## BTW, why the heck are we being run in a shutdown runlevel?!
if test x${RL} = x0 || test x${RL} = x6 ; then
    FORCE=yes
    RETRY=yes
    POLICYHELPER=
    BEQUIET=
    printerror ----------------------------------------------------
    printerror WARNING: invoke-rc.d called during shutdown sequence
    printerror enabling safe mode: initscript policy layer disabled
    printerror ----------------------------------------------------
fi

## Verifies the existance of proper S??initscriptID and K??initscriptID 
## *links* in the proper /etc/rc?.d/ directory
verifyrclink () {
  #
  # verifies if parameters are non-dangling symlinks
  # all parameters are verified
  #
  doexit=
  while test $# -gt 0 ; do
    if test ! -L "$1" ; then
        printerror not a symlink: $1
        doexit=102
    fi
    if test ! -f "$1" ; then
        printerror dangling symlink: $1
        doexit=102
    fi
    shift
  done
  if test x${doexit} != x && test x${RETRY} = x; then
     exit ${doexit}
  fi
  return 0
}

# we do handle multiple links per runlevel
# but we don't handle embedded blanks in link names :-(
if test x${RL} != x ; then
    SLINK=`ls -d -Q ${RCDPREFIX}${RL}.d/S[0-9][0-9]${INITSCRIPTID} 2>/dev/null | xargs`
    KLINK=`ls -d -Q ${RCDPREFIX}${RL}.d/K[0-9][0-9]${INITSCRIPTID} 2>/dev/null | xargs`
    SSLINK=`ls -d -Q ${RCDPREFIX}S.d/S[0-9][0-9]${INITSCRIPTID} 2>/dev/null | xargs`

    verifyrclink ${SLINK} ${KLINK} ${SSLINK}
fi

testexec () {
  #
  # returns true if any of the parameters is
  # executable (after following links)
  #
  while test $# -gt 0 ; do
    if test -x "$1" ; then
       return 0
    fi
    shift
  done
  return 1
}

RC=

###
### LOCAL INITSCRIPT POLICY: Enforce need of a start entry
### in either runlevel S or current runlevel to allow start
### or restart.
###
case ${ACTION} in
  start|restart)
    if testexec ${SLINK} ; then
	RC=104
    elif testexec ${KLINK} ; then
	RC=101
    elif testexec ${SSLINK} ; then
	RC=104
    fi
  ;;
esac

# test if /etc/init.d/initscript is actually executable
if testexec "${INITDPREFIX}${INITSCRIPTID}" ; then
    if test x${RC} = x && test x${MODE} = xquery ; then
        RC=105
    fi

    # call policy layer
    querypolicy
    case ${RC} in
        101|104)
           ;;
        *) if test x${MODE} != xquery ; then
	       printerror policy-rc.d returned error status ${RC}
	       if test x${RETRY} = x ; then
	           exit ${RC}
               else
    	           RC=102
    	       fi
           fi
           ;;
    esac
else
    ###
    ### LOCAL INITSCRIPT POLICY: non-executable initscript; deny exec.
    ### (this is common sense, actually :^P )
    ###
    RC=101
fi

## Handles --query
if test x${MODE} = xquery ; then
    exit ${RC}
fi


setechoactions () {
    if test $# -gt 1 ; then
	echoaction=true
    else
	echoaction=
    fi
}
getnextaction () {
    saction=$1
    shift
    ACTION="$@"
}

## Executes initscript
## note that $ACTION is a space-separated list of actions
## to be attempted in order until one suceeds.
if test x${FORCE} != x || test ${RC} -eq 104 ; then
    if testexec "${INITDPREFIX}${INITSCRIPTID}" ; then
	RC=102
	setechoactions ${ACTION}
	while test ! -z "${ACTION}" ; do
	    getnextaction ${ACTION}
	    if test ! -z ${echoaction} ; then
		printerror executing initscript action \"${saction}\"...
	    fi

	    "${INITDPREFIX}${INITSCRIPTID}" "${saction}" "$@" && exit 0
	    RC=$?

	    if test ! -z "${ACTION}" ; then
		printerror action \"${saction}\" failed, trying next action...
	    fi
	done
	printerror initscript ${INITSCRIPTID}, action \"${saction}\" failed.
	exit ${RC}
    fi
    exit 102
fi

## Handles --disclose-deny
if test ${RC} -eq 101 && test x${RETURNFAILURE} = x ; then
    RC=0
else
    formataction ${ACTION}
    printerror initscript ${naction} \"${printaction}\" not executed.
fi

exit ${RC}
```

---

### Post by leosr on 2009-06-16
Posiblemente el próximo fin de semana reinstale Ubuntu, para ver si se soluciona este problema, lo haría conservando el /home y haciendo una copia desde Synaptic de todos los paquetes instalados (así fué como actualicé de Intrepid a Jaunty).
La duda que tengo es que si con este método vá a saltar este problema nuevamente o si es mejor instalar programa por programa (lo que es muy engorroso).

Cada ves que instalo algo sigue tirando ese maldito error con NFS. Hoy cuando instalé un paquete, hice que mande el informe de error a Launchpad.

Gracias a todos por la ayuda, después les cuento si se solucionó este problema.

---

### Post by guillermolisi on 2009-06-17
> **leosr said:**
> Posiblemente el próximo fin de semana reinstale Ubuntu, para ver si se soluciona este problema, lo haría conservando el /home y haciendo una copia desde Synaptic de todos los paquetes instalados (así fué como actualicé de Intrepid a Jaunty).
La duda que tengo es que si con este método vá a saltar este problema nuevamente o si es mejor instalar programa por programa (lo que es muy engorroso).

Cada ves que instalo algo sigue tirando ese maldito error con NFS. Hoy cuando instalé un paquete, hice que mande el informe de error a Launchpad.

Gracias a todos por la ayuda, después les cuento si se solucionó este problema.
Compare el contenido de ese archivo con los que poseen las dos maquinas que uso con NFS (en distintas LANs) y esta exactamente igual, no le sobra ni falta nada.

Raro ....(se me quemaron los papeles :( )

---

### Post by leosr on 2009-06-17
> **guillermolisi said:**
> Compare el contenido de ese archivo con los que poseen las dos maquinas que uso con NFS (en distintas LANs) y esta exactamente igual, no le sobra ni falta nada.

Raro ....(se me quemaron los papeles :( )
Gracias Guille! Voy a probar re-instalando a ver que pasa.

Salu2

---

### Post by leosr on 2009-06-22
Bueno... reinstalé Ubuntu y ahora al parecer funciona, por lo menos NSF se instaló sin tirar ningún error. Al primer intento no lo pude hacer andar. Cuando tenga tiempo lo vuelvo a intentar.
Unas preguntontas... cómo hago para ver la carpeta compartida del servidor en la PC cliente? El cliente usa LXDE y como navegador de archivos predeterminado PCman.
También seguí el tutorial para compartir impresoras y no me funcionó.
Cómo sé que la red está funcionando y que las máquinas se pueden "ver"?

Gracias por la paciencia!

---

### Post by guillermolisi on 2009-06-22
> **leosr said:**
> Bueno... reinstalé Ubuntu y ahora al parecer funciona, por lo menos NSF se instaló sin tirar ningún error. Al primer intento no lo pude hacer andar. Cuando tenga tiempo lo vuelvo a intentar.
Unas preguntontas... cómo hago para ver la carpeta compartida del servidor en la PC cliente? El cliente usa LXDE y como navegador de archivos predeterminado PCman.
También seguí el tutorial para compartir impresoras y no me funcionó.
Cómo sé que la red está funcionando y que las máquinas se pueden "ver"?

Gracias por la paciencia!
SI conoces las direcciones IP de las otras maquinas hay un sencillo mecanismo para confirmar que hay comunicacion de datos entre ellas.

En una consola/terminal pone ```
ping direccion_ip_de_la_otra_maquina
```

Si tenes respuesta con 0 paquetes perdidos, esta todo fenomeno.

---

### Post by leosr on 2009-06-23
> **guillermolisi said:**
> SI conoces las direcciones IP de las otras maquinas hay un sencillo mecanismo para confirmar que hay comunicacion de datos entre ellas.

En una consola/terminal pone ```
ping direccion_ip_de_la_otra_maquina
```

Si tenes respuesta con 0 paquetes perdidos, esta todo fenomeno.

Aparentemente hay respuesta. Cómo hago que pare? xq sigue tirando el ping.
Me parece que el problema es que la ip de la máquina cliente cambia cuando la enciendo, configuré NSF con esta ip 192.168.1.34. Ahora hago un ifconfig y sale que está en 192.168.1.35. A lo mejor tendría que configurar el router para que deje la ip fija, para eso tengo que saber la mac de la placa de red, cómo la averiguo?
En la configuración de NSF, si en lugar de poner la ip pongo el nombre que tiene asignado el equipo cliente, no debería resolver la ip?

Cómo veo la carpeta compartida usando LXDE de la máquina? 

Gracias!

---

### Post by guillermolisi on 2009-06-23
> **leosr said:**
> Aparentemente hay respuesta. Cómo hago que pare? xq sigue tirando el ping.
Me parece que el problema es que la ip de la máquina cliente cambia cuando la enciendo, configuré NSF con esta ip 192.168.1.34. Ahora hago un ifconfig y sale que está en 192.168.1.35. A lo mejor tendría que configurar el router para que deje la ip fija, para eso tengo que saber la mac de la placa de red, cómo la averiguo?
En la configuración de NSF, si en lugar de poner la ip pongo el nombre que tiene asignado el equipo cliente, no debería resolver la ip?

Cómo veo la carpeta compartida usando LXDE de la máquina? 

Gracias!

Para parar el ping (o practicamente cualquier otro comando en consola, tenes que accionar las teclas Ctrl+c.

Si la asignacion de IP en esa maquina es dinamica, por eso puede ser que cambie cada vez que la encendes, podes asignarle una IP fija fuera del rango que se asigna via DHCP (dinamicamente) asi siempre tendra el mismo valor y te ahorras de usar la MAC address de la placa de red.

Si igual queres usar la MAC address, generalmente esta en una etiqueta en la misma placa. Sino la podes obtener con el comando ifconfig:
```
guille@guillepc:~$ ifconfig
eth0      Link encap:Ethernet  [COLOR="Red"]HWaddr 00:1a:92:4e:68:9b[/COLOR]
```

Si pones el nombre en la linea donde se monta el recurso publicado por NFS y no hay ningun servicio y/o archivo que traduzca correctamente ese nombre por la direccion IP adecuada, no va a funcionar.

---

### Post by leosr on 2009-07-01
Hola.
Volviendo a intentar...
En archivo /etc/exports de la máquina servidor puse lo siguiente:
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/leo/Documentos 192.168.1.33(rw,no_subtree_check,sync)
```
Osea, quiero que la pc cliente pueda accesar a la carpeta Documentos del servidor. Este tiene el IP 192.168.1.33 y el cliente 192.168.1.34

En el cliente modifiqué el archivo fstab con lo siguiete:
```
b: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=642314bd-ffa2-401f-9fb2-128d25d51f90 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=18889ba5-9e13-440f-b430-c9a98d198753 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=157f3a48-5d97-45b1-933a-38c01e79da7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
192.168.1.33:/home/leo/Documentos  /home/leo/Documentos  nfs user,uid=1000,noauto,rsize=4096,wsize=4096,noatim

```
Está configurado según el tutorial [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)

Hay algo que esté mal?

Salu2

---

### Post by leosr on 2009-07-01
```
zg@Celeron-desktop:~$ sudo mount -a
[sudo] password for zg:
zg@Celeron-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
zg@Celeron-desktop:~$
```

No veo que aparezca la carpeta compartida.

Al hacer un ping en las 2 pcs no hay paquetes perdidos, es decir que se comunican.

En el tutorial, después que se edita el archivo /etc/exports sigue la verificación:
```
leo@Semprom2600-desktop:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [ OK ] 
leo@Semprom2600-desktop:~$ sudo exports
sudo: exports: command not found
leo@Semprom2600-desktop:~$ 
```

No reconoce el comando exports.

En el tutorial dice lo siguiente:
```
En este caso se compatirá la carpeta "/var/www/htdocs" a la ip del equipo del desarroyador web "10.0.0.6" para que este pueda editar el contenido del mismo (el uid y gid en el cliente/servidor son los mismos).
```
Tendrá algo que ver el uid y gid? Cómo sé que en los 2 equipos es el mismo?
Espero que sea el último edit ;)

---

### Post by guillermolisi on 2009-07-01
> **leosr said:**
> Hola.
Volviendo a intentar...
En archivo /etc/exports de la máquina servidor puse lo siguiente:
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/leo/Documentos 192.168.1.33(rw,no_subtree_check,sync)
```
Osea, quiero que la pc cliente pueda accesar a la carpeta Documentos del servidor. Este tiene el IP 192.168.1.33 y el cliente 192.168.1.34

En el cliente modifiqué el archivo fstab con lo siguiete:
```
b: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=642314bd-ffa2-401f-9fb2-128d25d51f90 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=18889ba5-9e13-440f-b430-c9a98d198753 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=157f3a48-5d97-45b1-933a-38c01e79da7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
192.168.1.33:/home/leo/Documentos  /home/leo/Documentos  nfs user,uid=1000,noauto,rsize=4096,wsize=4096,noatim

```
Está configurado según el tutorial [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)

Hay algo que esté mal?

Salu2
Proba con las siguientes opciones:

En la maquina cliente, en /etc/fstab, usa solamente rw,user,auto.

En el archivo /etc/exports, en el server, usa rw,insecure,sync,no_root_squash.

Reinicia el NFS server (sudo /etc/init.d/nfs restart) y volve a montar en el cliente.

Si no recuerdo mal, en /var/log/dmesg y/o /var/log/messages se registran problemas al montar unidades compartidas. Ahi deberias encontrar mas informacion.

---

### Post by leosr on 2009-07-01
Hice los cambios que sugeriste...
en el servidor sale lo siguiente:
```
leo@Semprom2600-desktop:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.33:/home/leo/Documentos".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 
leo@Semprom2600-desktop:~$
```

Y en el cliente:
```
zg@Celeron-desktop:~$ sudo mount -a
mount.nfs: mount point /home/leo/Documentos does not exist
zg@Celeron-desktop:~$
```

De cuál de las 2 máquinas querés  que muestre el log?

---

### Post by staar on 2009-07-01
en el cliente tenés que crear previamente la carpeta /home/leo/Documentos para que lo pueda montar...

saludos

---

### Post by leosr on 2009-07-01
> **staar said:**
> en el cliente tenés que crear previamente la carpeta /home/leo/Documentos para que lo pueda montar...

saludos
Ah! y en qué carpeta la creo?
Puede ser /home (de la máquina cliente) /leo/Documentos?

---

### Post by staar on 2009-07-01
en el cliente, en tu home o carpeta personal (la ruta es /home/leo) tenés que crear la carpeta Documentos (respetando las mayúsculas)

saludos

---

### Post by leosr on 2009-07-01
> **staar said:**
> en el cliente, en tu home o carpeta personal (la ruta es /home/leo) tenés que crear la carpeta Documentos (respetando las mayúsculas)

saludos

Ok. Creé la carpeta en /home/zg/leo/Documentos, zg es el nombre de usuario de la máquina cliente. Modifiqué el archivo fstab, ahora quedó así:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=642314bd-ffa2-401f-9fb2-128d25d51f90 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=18889ba5-9e13-440f-b430-c9a98d198753 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=157f3a48-5d97-45b1-933a-38c01e79da7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
192.168.1.33:/home/leo/Documentos  /home/zg/leo/Documentos  nfs user,auto,rw
```

Luego ejecuto lo siguiente:
```
zg@Celeron-desktop:~$ sudo mount -a
mount.nfs: access denied by server while mounting 192.168.1.33:/home/leo/Documentos
zg@Celeron-desktop:~$
```

---

### Post by staar on 2009-07-01
volvé a poner las opciones como estaban en el tutorial (pero manteniendo el cambio a /home/zg/leo/Documentos) en el servidor y en el cliente, reiniciá nfs y fijate...

saludos

---

### Post by guillermolisi on 2009-07-01
> **leosr said:**
> Ok. Creé la carpeta en /home/zg/leo/Documentos, zg es el nombre de usuario de la máquina cliente. Modifiqué el archivo fstab, ahora quedó así:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=642314bd-ffa2-401f-9fb2-128d25d51f90 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=18889ba5-9e13-440f-b430-c9a98d198753 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=157f3a48-5d97-45b1-933a-38c01e79da7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
192.168.1.33:/home/leo/Documentos  /home/zg/leo/Documentos  nfs user,auto,rw
```

Luego ejecuto lo siguiente:
```
zg@Celeron-desktop:~$ sudo mount -a
mount.nfs: access denied by server while mounting 192.168.1.33:[COLOR="Red"]/home/leo/Documentos[/COLOR]
zg@Celeron-desktop:~$
```

Fijate en /var/log/dmesg de la maquna cliente, a ver si sale algun mensaje relacionado con el montaje de lo que remarque en color.

En una consola/terminal podes ingresar dmesg y te muestra los ultimos registros de ese archivo de log.

---

### Post by leosr on 2009-07-01
> **staar said:**
> volvé a poner las opciones como estaban en el tutorial (pero manteniendo el cambio a /home/zg/leo/Documentos) en el servidor y en el cliente, reiniciá nfs y fijate...

saludos

Sólo en el archivo fstab del cliente puse /home/zg/leo/Documentos. En el archivo exports del servidor puse /home/leo/Documentos 192.168.1.33(rw,no_subtree_check,sync)
No sé si te refirís a eso.

---

### Post by leosr on 2009-07-01
> **staar said:**
> volvé a poner las opciones como estaban en el tutorial (pero manteniendo el cambio a /home/zg/leo/Documentos) en el servidor y en el cliente, reiniciá nfs y fijate...

saludos

> **guillermolisi said:**
> Fijate en /var/log/dmesg de la maquna cliente, a ver si sale algun mensaje relacionado con el montaje de lo que remarque en color.

En una consola/terminal podes ingresar dmesg y te muestra los ultimos registros de ese archivo de log.

Acá vá lo que dice dmesg:
```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000b7f0000 (usable)
[    0.000000]  BIOS-e820: 000000000b7f0000 - 000000000b7f8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000b7f8000 - 000000000b800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.1 present.
[    0.000000] last_pfn = 0xb7f0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000b7f0000 (usable)
[    0.000000]  modified: 000000000b7f0000 - 000000000b7f8000 (ACPI data)
[    0.000000]  modified: 000000000b7f8000 - 000000000b800000 (ACPI NVS)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to b7f0000 @ 10000-16000
[    0.000000] RAMDISK: 0b0a1000 - 0b7dfa8c
[    0.000000] ACPI: RSDP 000FE030, 0014 (r0 Acer  )
[    0.000000] ACPI: RSDT 0B7F0000, 0028 (r1 Acer   V76M            1 Acer        0)
[    0.000000] ACPI: FACP 0B7F0028, 0074 (r1 Acer   V76M            1 Acer        0)
[    0.000000] ACPI: DSDT 0B7F00A0, 1CC1 (r1   Acer   V76M       1000 MSFT  100000A)
[    0.000000] ACPI: FACS 0B7F8000, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 183MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0b7f0000
[    0.000000]   low ram: 00000000 - 0b7f0000
[    0.000000]   bootmap 00012000 - 00013700
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000b7f0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [000b0a1000 - 000b7dfa8c]          RAMDISK ==> [000b0a1000 - 000b7dfa8c]
[    0.000000]   #5 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000b7f0
[    0.000000]   HighMem  0x0000b7f0 -> 0x0000b7f0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0000b7f0
[    0.000000] On node 0 totalpages: 46965
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 336 pages used for memmap
[    0.000000]   Normal zone: 42656 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0xf008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: b800000:f47f0000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 46597
[    0.000000] Kernel command line: root=UUID=642314bd-ffa2-401f-9fb2-128d25d51f90 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 699.926 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 941760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 169984k/188352k available (4110k kernel code, 17768k reserved, 2197k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xcbff0000 - 0xff3fe000   ( 820 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcb7f0000   ( 183 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004095] Calibrating delay loop (skipped), value calculated using timer frequency.. 1399.85 BogoMIPS (lpj=2799704)
[    0.004298] Security Framework initialized
[    0.004409] SELinux:  Disabled at boot.
[    0.004651] AppArmor: AppArmor initialized
[    0.004721] Mount-cache hash table entries: 512
[    0.006237] Initializing cgroup subsys ns
[    0.006309] Initializing cgroup subsys cpuacct
[    0.006320] Initializing cgroup subsys memory
[    0.006352] Initializing cgroup subsys freezer
[    0.006490] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.006500] CPU: L2 cache: 128K
[    0.006742] Checking 'hlt' instruction... OK.
[    0.022299] SMP alternatives: switching to UP code
[    0.915961] Freeing SMP alternatives: 18k freed
[    0.916171] ACPI: Core revision 20080926
[    0.920542] ACPI: Checking initramfs for custom DSDT
[    1.920093] ACPI: setting ELCR to 0200 (from 0e20)
[    1.924915] weird, boot CPU (#0) not listedby the BIOS.
[    1.924936] SMP motherboard not detected.
[    1.924955] Local APIC not detected. Using dummy APIC emulation.
[    1.924965] SMP disabled
[    1.930455] Brought up 1 CPUs
[    1.930524] Total of 1 processors activated (1399.85 BogoMIPS).
[    1.930747] CPU0 attaching NULL sched-domain.
[    1.934811] net_namespace: 776 bytes
[    1.934871] Booting paravirtualized kernel on bare hardware
[    1.936625] Time: 16:31:25  Date: 07/01/09
[    1.936697] regulator: core version 0.5
[    1.937240] NET: Registered protocol family 16
[    1.938383] EISA bus registered
[    1.938587] ACPI: bus type pci registered
[    1.942612] PCI: PCI BIOS revision 2.10 entry at 0xf0200, last bus=1
[    1.942627] PCI: Using configuration type 1 for base access
[    1.950307] ACPI: EC: Look up EC in DSDT
[    1.961622] ACPI: Interpreter enabled
[    1.961672] ACPI: (supports S0 S1 S5)
[    1.961737] ACPI: Using PIC for interrupt routing
[    1.982553] ACPI: No dock devices found.
[    1.982641] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.982959] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    1.983161] pci 0000:00:00.1: reg 10 io port: [0x1f0-0x1f7]
[    1.983177] pci 0000:00:00.1: reg 14 io port: [0x3f4-0x3f7]
[    1.983191] pci 0000:00:00.1: reg 18 io port: [0x170-0x177]
[    1.983206] pci 0000:00:00.1: reg 1c io port: [0x374-0x377]
[    1.983220] pci 0000:00:00.1: reg 20 io port: [0x9420-0x942f]
[    1.983468] pci 0000:00:01.2: reg 10 32bit mmio: [0x81300000-0x81300fff]
[    1.983636] pci 0000:00:09.0: reg 10 32bit mmio: [0x80100000-0x8010ffff]
[    1.983652] pci 0000:00:09.0: reg 14 io port: [0x7000-0x7007]
[    1.983708] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.983725] pci 0000:00:09.0: PME# disabled
[    1.983789] pci 0000:00:0b.0: reg 10 io port: [0x7400-0x74ff]
[    1.983804] pci 0000:00:0b.0: reg 14 32bit mmio: [0x80110000-0x801100ff]
[    1.983853] pci 0000:00:0b.0: supports D1 D2
[    1.983860] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot
[    1.983872] pci 0000:00:0b.0: PME# disabled
[    1.983934] pci 0000:00:0c.0: reg 10 io port: [0x9000-0x903f]
[    1.984094] pci 0000:00:0c.0: reg 14 io port: [0x9050-0x905f]
[    1.984110] pci 0000:00:0c.0: reg 18 io port: [0x9070-0x907f]
[    1.984125] pci 0000:00:0c.0: reg 1c io port: [0x9090-0x9093]
[    1.984140] pci 0000:00:0c.0: reg 20 io port: [0x90a4-0x90a7]
[    1.984179] pci 0000:00:0c.0: supports D1 D2
[    1.984357] pci 0000:01:00.0: reg 10 32bit mmio: [0x80800000-0x80ffffff]
[    1.984372] pci 0000:01:00.0: reg 14 32bit mmio: [0x80500000-0x8050ffff]
[    1.984386] pci 0000:01:00.0: reg 18 io port: [0x8000-0x807f]
[    1.984426] pci 0000:01:00.0: supports D2
[    1.984491] pci 0000:00:02.0: bridge io port: [0x8000-0x8fff]
[    1.984505] pci 0000:00:02.0: bridge 32bit mmio: [0x80500000-0x805fffff]
[    1.984519] pci 0000:00:02.0: bridge 32bit mmio pref: [0x80600000-0x810fffff]
[    1.984544] bus 00 -> node 0
[    1.984637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.988471] ACPI: PCI Interrupt Link [PILA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    1.989131] ACPI: PCI Interrupt Link [PILB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    1.989585] ACPI: PCI Interrupt Link [PILC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    1.990121] ACPI: PCI Interrupt Link [PILD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    1.990659] ACPI: PCI Interrupt Link [PILE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    1.991435] ACPI: WMI: Mapper loaded
[    1.993223] SCSI subsystem initialized
[    1.994087] libata version 3.00 loaded.
[    1.994791] usbcore: registered new interface driver usbfs
[    1.995044] usbcore: registered new interface driver hub
[    1.995628] usbcore: registered new device driver usb
[    1.997263] PCI: Using ACPI for IRQ routing
[    1.998104] Bluetooth: Core ver 2.13
[    1.998104] NET: Registered protocol family 31
[    1.998104] Bluetooth: HCI device and connection manager initialized
[    1.998104] Bluetooth: HCI socket layer initialized
[    1.998104] NET: Registered protocol family 8
[    1.998104] NET: Registered protocol family 20
[    1.998104] NetLabel: Initializing
[    1.998104] NetLabel:  domain hash size = 128
[    1.998104] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.998104] NetLabel:  unlabeled traffic allowed by default
[    2.001035] AppArmor: AppArmor Filesystem Enabled
[    2.001459] pnp: PnP ACPI init
[    2.001646] ACPI: bus type pnp registered
[    2.021349] pnp: PnP ACPI: found 12 devices
[    2.021369] ACPI: ACPI bus type pnp unregistered
[    2.021390] PnPBIOS: Disabled by ACPI PNP
[    2.021503] system 00:0b: ioport range 0xf000-0xf03f has been reserved
[    2.021514] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    2.021524] system 00:0b: ioport range 0xf00-0xf01 has been reserved
[    2.021533] system 00:0b: ioport range 0x1700-0x1701 has been reserved
[    2.021543] system 00:0b: ioport range 0x1f00-0x1f01 has been reserved
[    2.021552] system 00:0b: ioport range 0x2700-0x2701 has been reserved
[    2.021562] system 00:0b: ioport range 0x2f00-0x2f01 has been reserved
[    2.021571] system 00:0b: ioport range 0x3700-0x3701 has been reserved
[    2.021580] system 00:0b: ioport range 0x3f00-0x3f01 has been reserved
[    2.021590] system 00:0b: ioport range 0x4700-0x4701 has been reserved
[    2.021599] system 00:0b: ioport range 0x4f00-0x4f01 has been reserved
[    2.021609] system 00:0b: ioport range 0x5700-0x5701 has been reserved
[    2.021618] system 00:0b: ioport range 0x5f00-0x5f01 has been reserved
[    2.021628] system 00:0b: ioport range 0x6700-0x6701 has been reserved
[    2.021637] system 00:0b: ioport range 0x6f00-0x6f01 has been reserved
[    2.021647] system 00:0b: ioport range 0xa700-0xa701 has been reserved
[    2.021656] system 00:0b: ioport range 0xaf00-0xaf01 has been reserved
[    2.021666] system 00:0b: ioport range 0xb700-0xb701 has been reserved
[    2.021676] system 00:0b: ioport range 0xbf00-0xbf01 has been reserved
[    2.021685] system 00:0b: ioport range 0xc700-0xc701 has been reserved
[    2.021695] system 00:0b: ioport range 0xcf00-0xcf01 has been reserved
[    2.021705] system 00:0b: ioport range 0xd700-0xd701 has been reserved
[    2.021714] system 00:0b: ioport range 0xdf00-0xdf01 has been reserved
[    2.021724] system 00:0b: ioport range 0xe700-0xe701 has been reserved
[    2.021734] system 00:0b: ioport range 0xef00-0xef01 has been reserved
[    2.021743] system 00:0b: ioport range 0xf700-0xf701 has been reserved
[    2.021753] system 00:0b: ioport range 0xff00-0xff01 has been reserved
[    2.021764] system 00:0b: iomem range 0x0-0x9ff could not be reserved
[    2.021773] system 00:0b: iomem range 0xe00-0xfff could not be reserved
[    2.021786] system 00:0b: iomem range 0xfffe0000-0xffffffff could not be reserved
[    2.021796] system 00:0b: iomem range 0x100000-0xffffff could not be reserved
[    2.021805] system 00:0b: iomem range 0x1000000-0xb7fffff could not be reserved
[    2.023041] PM-Timer had inconsistent results: 0x0x16b76d, 0x0x16b36e - aborting.
[    2.023181] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    2.023191] pci 0000:00:02.0:   IO window: 0x8000-0x8fff
[    2.023214] pci 0000:00:02.0:   MEM window: 0x80500000-0x805fffff
[    2.023228] pci 0000:00:02.0:   PREFETCH window: 0x00000080600000-0x000000810fffff
[    2.023291] pci 0000:00:02.0: setting latency timer to 64
[    2.023313] bus: 00 index 0 io port: [0x00-0xffff]
[    2.023321] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    2.023330] bus: 01 index 0 io port: [0x8000-0x8fff]
[    2.023337] bus: 01 index 1 mmio: [0x80500000-0x805fffff]
[    2.023344] bus: 01 index 2 mmio: [0x80600000-0x810fffff]
[    2.023351] bus: 01 index 3 mmio: [0x0-0x0]
[    2.023488] NET: Registered protocol family 2
[    2.024839] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    2.026658] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    2.027896] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    2.029395] TCP: Hash tables configured (established 8192 bind 8192)
[    2.029438] TCP reno registered
[    2.031198] NET: Registered protocol family 1
[    2.032687] checking if image is initramfs... it is
[    5.174873] Freeing initrd memory: 7418k freed
[    5.175606] cpufreq: No nForce2 chipset.
[    5.177457] audit: initializing netlink socket (disabled)
[    5.177673] type=2000 audit(1246465888.176:1): initialized
[    5.207888] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    5.215464] VFS: Disk quotas dquot_6.5.1
[    5.216296] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.223040] fuse init (API version 7.10)
[    5.223867] msgmni has been set to 346
[    5.226800] alg: No test for stdrng (krng)
[    5.227019] io scheduler noop registered
[    5.227031] io scheduler anticipatory registered
[    5.227039] io scheduler deadline registered
[    5.227452] io scheduler cfq registered (default)
[    5.227918] pci 0000:01:00.0: Boot video device
[    5.243628] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    5.243675] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    5.244740] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    5.244760] ACPI: Power Button (FF) [PWRF]
[    5.246068] processor ACPI_CPU:00: registered as cooling_device0
[    5.254641] isapnp: Scanning for PnP cards...
[    5.609618] isapnp: No Plug & Play device found
[    5.617422] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    5.617941] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.618268] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    5.619691] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    5.620223] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.625746] brd: module loaded
[    5.628574] loop: module loaded
[    5.629780] Fixed MDIO Bus: probed
[    5.629834] PPP generic driver version 2.4.2
[    5.630469] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    5.630786] Driver 'sd' needs updating - please use bus_type methods
[    5.630848] Driver 'sr' needs updating - please use bus_type methods
[    5.633918] pata_sis 0000:00:00.1: version 0.5.2
[    5.634025] pata_sis 0000:00:00.1: can't derive routing for PCI INT A
[    5.636299] scsi0 : pata_sis
[    5.637578] scsi1 : pata_sis
[    5.638065] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x9420 irq 14
[    5.638079] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x9428 irq 15
[    5.801541] ata1.00: ATA-5: ST320423A, 3.02, max UDMA/66
[    5.801558] ata1.00: 40011300 sectors, multi 32: LBA
[    5.817268] ata1.00: configured for UDMA/66
[    5.984682] ata2.01: ATAPI: CD-ROM 48X/AKU, T31, max MWDMA2, CDB intr
[    6.001090] ata2.01: configured for PIO4
[    6.002856] scsi 0:0:0:0: Direct-Access     ATA      ST320423A        3.02 PQ: 0 ANSI: 5
[    6.004385] sd 0:0:0:0: [sda] 40011300 512-byte hardware sectors: (20.4 GB/19.0 GiB)
[    6.004592] sd 0:0:0:0: [sda] Write Protect is off
[    6.004604] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.005015] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.005991] sd 0:0:0:0: [sda] 40011300 512-byte hardware sectors: (20.4 GB/19.0 GiB)
[    6.006160] sd 0:0:0:0: [sda] Write Protect is off
[    6.006170] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.006382] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.006423]  sda: sda1 sda2 < sda5 sda6 >
[    6.067784] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.068311] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.070148] scsi 1:0:1:0: CD-ROM            E-IDE    CD-ROM 48X/AKU   T31  PQ: 0 ANSI: 5
[    6.075990] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[    6.076029] Uniform CD-ROM driver Revision: 3.20
[    6.077223] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    6.077745] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    6.078802] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.078956] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.080230] ACPI: PCI Interrupt Link [PILE] enabled at IRQ 9
[    6.080252] PCI: setting IRQ 9 as level-triggered
[    6.080266] ohci_hcd 0000:00:01.2: PCI INT A -> Link[PILE] -> GSI 9 (level, low) -> IRQ 9
[    6.080458] ohci_hcd 0000:00:01.2: OHCI Host Controller
[    6.081765] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    6.082022] ohci_hcd 0000:00:01.2: irq 9, io mem 0x81300000
[    6.139514] usb usb1: configuration #1 chosen from 1 choice
[    6.139714] hub 1-0:1.0: USB hub found
[    6.139881] hub 1-0:1.0: 2 ports detected
[    6.141105] uhci_hcd: USB Universal Host Controller Interface driver
[    6.141936] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    6.143760] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.143879] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.145149] mice: PS/2 mouse device common for all mice
[    6.146282] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    6.146402] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    6.147120] device-mapper: uevent: version 1.0.3
[    6.149042] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    6.150077] device-mapper: multipath: version 1.0.5 loaded
[    6.150116] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.151188] EISA: Probing bus 0 at eisa.0
[    6.151277] Cannot allocate resource for EISA slot 7
[    6.151284] Cannot allocate resource for EISA slot 8
[    6.151291] EISA: Detected 0 cards.
[    6.151649] cpuidle: using governor ladder
[    6.151663] cpuidle: using governor menu
[    6.154904] TCP cubic registered
[    6.155788] NET: Registered protocol family 10
[    6.158764] lo: Disabled Privacy Extensions
[    6.160313] NET: Registered protocol family 17
[    6.160656] Bluetooth: L2CAP ver 2.11
[    6.160665] Bluetooth: L2CAP socket layer initialized
[    6.160682] Bluetooth: SCO (Voice Link) ver 0.6
[    6.160688] Bluetooth: SCO socket layer initialized
[    6.161774] Bluetooth: RFCOMM socket layer initialized
[    6.161917] Bluetooth: RFCOMM TTY layer initialized
[    6.161927] Bluetooth: RFCOMM ver 1.10
[    6.162686] IO APIC resources could be not be allocated.
[    6.162827] Using IPI No-Shortcut mode
[    6.163901] registered taskstats version 1
[    6.164590]   Magic number: 1:255:539
[    6.165200] rtc_cmos 00:05: setting system clock to 2009-07-01 16:31:30 UTC (1246465890)
[    6.165215] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.165222] EDD information not available.
[    6.177449] Freeing unused kernel memory: 532k freed
[    6.178236] Write protecting the kernel text: 4112k
[    6.178389] Write protecting the kernel read-only data: 1524k
[    6.201036] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    8.446942] Floppy drive(s): fd0 is 1.44M
[    8.464246] FDC 0 is a post-1991 82077
[    9.454919] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    9.455130] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    9.504095] 8139too Fast Ethernet driver 0.9.28
[    9.505791] ACPI: PCI Interrupt Link [PILB] enabled at IRQ 10
[    9.505813] PCI: setting IRQ 10 as level-triggered
[    9.505831] 8139too 0000:00:0b.0: PCI INT A -> Link[PILB] -> GSI 10 (level, low) -> IRQ 10
[    9.509048] eth0: RealTek RTL8139 at 0x7400, 00:08:54:b1:0f:b4, IRQ 10
[    9.509071] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   13.330637] PM: Starting manual resume from disk
[   13.330679] PM: Resume from partition 8:5
[   13.330686] PM: Checking hibernation image.
[   13.331882] PM: Resume from disk failed.
[   13.418916] EXT4-fs: barriers enabled
[   13.434048] kjournald2 starting.  Commit interval 5 seconds
[   13.434287] EXT4-fs: delayed allocation enabled
[   13.434297] EXT4-fs: file extents enabled
[   13.437442] EXT4-fs: mballoc enabled
[   13.437567] EXT4-fs: mounted filesystem with ordered data mode.
[   22.757711] udev: starting version 141
[   23.804602] parport_pc 00:08: reported by Plug and Play ACPI
[   23.804738] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   24.014894] Linux agpgart interface v0.103
[   24.132492] agpgart-sis 0000:00:00.0: SiS chipset [1039/0620]
[   24.167739] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   24.429070] ACPI: I/O resource sis5595_smbus [0xf038-0xf039] conflicts with ACPI region PMU0 [0xf000-0xf03f]
[   24.429098] ACPI: Device needs an ACPI driver
[   24.473770] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted.
[   24.647723] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.638270] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   25.825913] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   26.321098] psmouse serio1: ID: 10 00 64<6>input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   28.760326] acer-wmi: Acer Laptop ACPI-WMI Extras
[   28.760400] acer-wmi: No or unsupported WMI interface, unable to load
[   28.968365] ACPI: PCI Interrupt Link [PILD] enabled at IRQ 5
[   28.968400] PCI: setting IRQ 5 as level-triggered
[   28.968417] ESS ES1938 (Solo-1) 0000:00:0c.0: PCI INT A -> Link[PILD] -> GSI 5 (level, low) -> IRQ 5
[   28.990568] gameport: ES1938 is pci0000:00:0c.0/gameport0, io 0x90a4, speed 1104kHz
[   30.104653] ppdev: user-space parallel port driver
[   32.029448] lp0: using parport0 (interrupt-driven).
[   32.979734] Adding 498004k swap on /dev/sda5.  Priority:-1 extents:1 across:498004k
[   33.945405] EXT4 FS on sda1, internal journal on sda1:8
[   36.365946] EXT4-fs: barriers enabled
[   36.381421] kjournald2 starting.  Commit interval 5 seconds
[   36.382439] EXT4 FS on sda6, internal journal on sda6:8
[   36.382456] EXT4-fs: delayed allocation enabled
[   36.382463] EXT4-fs: file extents enabled
[   36.391179] EXT4-fs: mballoc enabled
[   36.391312] EXT4-fs: mounted filesystem with ordered data mode.
[   38.094449] type=1505 audit(1246465922.425:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1756
[   38.097276] type=1505 audit(1246465922.429:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1756
[   38.098764] type=1505 audit(1246465922.429:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1756
[   38.100779] type=1505 audit(1246465922.433:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1756
[   38.998235] type=1505 audit(1246465923.330:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1761
[   39.002513] type=1505 audit(1246465923.334:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1761
[   39.248649] type=1505 audit(1246465923.582:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1765
[   47.891087] RPC: Registered udp transport module.
[   47.891115] RPC: Registered tcp transport module.
[   48.232527] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   48.757514] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   48.767769] NFSD: starting 90-second grace period
[   55.656156] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   55.656198] Bluetooth: BNEP filters: protocol multicast
[   55.834460] Bridge firewalling registered
[   62.673684] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1


```

---

### Post by Mister X on 2009-07-01
en el archivos exports del servidor tenes que poner a que maquinas vas a compartir el recurso, osea las maquinas clientes (en este caso la 192.168.1.34), corregí eso.

---

### Post by leosr on 2009-07-01
Guille, la carpeta que quiero compartir es /home/leo/Documentos, donde leo es el usuario del server. Y 194.168.1.33 es la IP del server.
Por qué te parece que está mal?

---

### Post by leosr on 2009-07-01
> **Mister X said:**
> en el archivos exports del servidor tenes que poner a que maquinas vas a compartir el recurso, osea las maquinas clientes (en este caso la 192.168.1.34), corregí eso.
Quedaría así?
/home/leo/Documentos 192.168.1.34(rw,no_subtree_check,sync)

---

### Post by leosr on 2009-07-01
> **Mister X said:**
> en el archivos exports del servidor tenes que poner a que maquinas vas a compartir el recurso, osea las maquinas clientes (en este caso la 192.168.1.34), corregí eso.

Capo! la pegaste!
Ahora anda.

Muchas gracias Guille y Staar. Gracias por la paciencia.
Por favor pongan el post como solved, no sé cómo se hace.

Aguante la Comunidad!! :lolflag: ):P

---

