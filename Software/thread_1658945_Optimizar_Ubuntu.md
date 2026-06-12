---
title: "Optimizar Ubuntu"
date: 2011-01-03
forum: Software
---

### Post by aleperno on 2011-01-03
Buenos Dias, poseeo una netbook ASUS que por razones de comododidas con la distro y cuestiones de gusto, le instalé la version desktop en vez de la netbook.

La cuestión es que de momentos lo noto un poco torpe y ando queriendo optimizar un poco la cosa.
 
Por alguna razon el menu de "efectos visuales" se encuentra bloqueado, no puedo elegir entre "ninguno, normal, extra".

Buscando un poco por el foro encontre este thread
 [http://ubuntuforums.org/showthread.php?t=778913&highlight=optimizar](http://ubuntuforums.org/showthread.php?t=778913&highlight=optimizar)

que tan confiable es? No me molestaría tener un tema estilo "Windows 95" mientras se gane eficiencia, así que si tienen sugerencias, sientanse libres :D

Muchas Gracias
Saludos

---

### Post by juancarlospaco on 2011-01-03
Spec del equipo ?

---

### Post by alfplayer on 2011-01-03
> **juancarlospaco said:**
> Spec del equipo ?

netbook?

Se puede desactivar servicios y cambiar a un entorno de escritorio más liviano.

---

### Post by juancarlospaco on 2011-01-03
Yo arrancaria por el Minimal CD... y ir armando a puro apt-getazo

---

### Post by aleperno on 2011-01-03
Asus EEEPC 1201HA
Intel Atom Z520 1.33 Ghz
2Gb ram
250 Gb

Que servicios le puedo desactivar?
Y como aliviano el entorno, cambiando de Ambience a uno mas berreta por ej?

Gracias por las respuestas.

Saludos

---

### Post by guillermolisi on 2011-01-04
Por el primer comentario pareceria que hay algun temita con la placa de video (que no se que marca y modelo es).
Los logs del sistema ayudan en estos casos: /var/log/Xorg.0.log; /var/log/dmesg serian los dos primeros a observar.

Complementariamente la seccion de video/VGA de la salida de "lshw" (sin las comillas) tambien ayudaria para saber sobre la placa de video.

Si no hay errores/warnings con el hardware, entonces recien ahi pasaria a optimizar procesos y servicios.

---

### Post by nomko on 2011-01-04
...

---

### Post by juancarlospaco on 2011-01-04
Tiene que andar bien el Ubuntu normal con esos spec... 
tal vez sin compiz x la vga, pero tiene que andar...

---

### Post by Wiredfixer on 2011-01-04
Compiz en una Netbook? No se me hace muy necesario.

Yo acabo de migrarme a Mint XFCE, La verdad, me funciona genial y no tengo nada de problemas a la hora de trabajar.

Antes tenia Ubuntu Gnome (10.04) y pues estaba bien, el problema es que empeze a tener problemas con la lectura de HDD, porque el equipo es algo "viejo" (Dell D620, me lo dieron en mi trabajo).

No se que diferencia tiene, pero la verdad, la senti mas ligera con XFCE que con Gnome, no se si Gnome use mucho la lectura del Disco, aun no me he documentado, pero la verdad es que el uso de disco suele alentar muchos procesos y ahora estoy muy bien.

Deberias probar la Version Netbook, en si lo unico distinto es la interfaz grafica, lo mas importante es como esta optimizado el sistema en su manera interna, la interfaz grafica la puedes cambiar si gustas al Modo "Normal".

Tambien deberias probar algo con [Swapiness]("https://help.ubuntu.com/community/SwapFaq") y pues recordar que una Netbook es para trabajo basico, no es una Notebook completa como para andarla cargando con Compiz y otros adornos.

---

### Post by losoollenos on 2011-01-06
Como sugirió juancarlospaco, y si realmente no te importa el aspecto w95, arrancá con el minimal cd, pero de 64 bits (si está soportado por ese micro, fijate).
Cuando termine la instalación del sistema base, arrancás el nuevo sistema, no hay gráfica, solo texto. Entonces te tenés que loguear y escribí:

sudo apt-get install gnome-core synaptic gdm 

Cuando termine esto podrás ingresar en modo grafico, bien feo, pero con lo necesario para seguir gráficamente con lo que necesites (office, reproductores, etc); asi realmente vas a tener un sistema que vuela, las optimizaciones que decís, son, por experiencia, prácticamente imperceptibles.

probalo !!!!

---

### Post by aleperno on 2011-01-07
Muchas gracias por las respuestas, voy a instalar el minimal en una notebook de pruebas que tengo a ver que tal.

Con el tema de los logs, se los pongo aca (si no es mucho problema) porque sinceramente no se interpretarlos.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux alejandro-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=ff1001eb-d0ec-4253-9369-bebfb7d54ee6 ro acpi_osi=Linux acpi_backlight=vendor quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  7 18:01:05 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:8108:1043:83ce Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller rev 7, Mem @ 0xf3f80000/524288, 0xd0000000/268435456, 0xf3f40000/262144, I/O @ 0x0000c880/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "psb"
(II) Loading /usr/lib/xorg/modules/drivers/psb_drv.so
(II) Module psb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.32.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) Debug: psbSetup
(II) PSB: driver for Intel GMA500 chipsets: Intel GMA500
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for psb
(II) Debug: psbProbe
(--) Assigning device section with no busID to primary device
(--) Chipset Intel GMA500 found
(II) PSB(0): Debug: Allocating new device
(II) PSB(0): Debug: psbPreInit
(II) PSB(0): psb_drv - 2.2.0.32L.0027
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) PSB(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) PSB(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(--) PSB(0): Linear framebuffer at 0x0
(==) PSB(0): RGB weight 888
(==) PSB(0): Default visual is TrueColor
(**) PSB(0): Option "ShadowFB" "true"
(==) PSB(0): Use hardware cursor.
(==) PSB(0): Not using ACPI for LVDS detection.
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) PSB(0): Debug: psbPreinitXpsb
(II) Loading sub module "Xpsb"
(II) LoadModule: "Xpsb"
(II) Loading /usr/lib/xorg/modules/drivers/Xpsb.so
(II) Module Xpsb: vendor="Tungsten Graphics Inc."
    compiled for 1.6.0, module version = 0.1.0
(II) PSB(0): Debug: psbDeviceScreenInit
(II) PSB(0): Debug: Initializing device
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) PSB(0): Debug: MMIO virtual address is 0xb780a000
(--) PSB(0): Mapped PCI MMIO at physical address 0xf3f80000
    with size 512 kiB
(EE) PSB(0): the stolenBase is:0x7f800000
(--) PSB(0): Detected 7932 kiB of "stolen" memory set aside as video RAM.
(EE) PSB(0): screnIndex is:0;fbPhys is:0x7f800000; fbsize is:0x007bf000
(--) PSB(0): Mapped graphics aperture at physical address 0x7f800000
    with size 7 MiB
(II) PSB(0): Debug: DRM device init
(II) PSB(0): Poulsbo MemClock 533, CoreClock 200
(II) PSB(0): Poulsbo Latencies 324 744 210 450
(II) PSB(0): sku_value is 0x00800000, sku_bSDVOEnable is 1, sku_bMaxResEnableInt is 0
(II) PSB(0): Debug: psbInitOutputs
(II) PSB(0): Debug: psbLVDSInit
(II) PSB(0): Output LVDS0 has no monitor section
(II) Debug: i830_psbOutputInit
(II) PSB(0): I2C bus "LVDSBLC_B" initialized.
(II) PSB(0): I2C bus "LVDSDDC_C" initialized.
(II) PSB(0): I2C device "LVDSBLC_B:BLC Control" registered at address 0x58.
(II) PSB(0): Debug: i830_psbDDCGetModes
(II) PSB(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) PSB(0): EDID for output LVDS0
(II) PSB(0): Manufacturer: HSD  Model: 4b6  Serial#: 6910
(II) PSB(0): Year: 2010  Week: 5
(II) PSB(0): EDID Version: 1.3
(II) PSB(0): Digital Display Input
(II) PSB(0): Max Image Size [cm]: horiz.: 27  vert.: 15
(II) PSB(0): Gamma: 2.20
(II) PSB(0): No DPMS capabilities specified
(II) PSB(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) PSB(0): First detailed timing is preferred mode
(II) PSB(0): redX: 0.591 redY: 0.354   greenX: 0.322 greenY: 0.547
(II) PSB(0): blueX: 0.153 blueY: 0.098   whiteX: 0.313 whiteY: 0.329
(II) PSB(0): Manufacturer's mask: 0
(II) PSB(0): Supported detailed timing:
(II) PSB(0): clock: 71.9 MHz   Image Size:  270 x 150 mm
(II) PSB(0): h_active: 1366  h_sync: 1414  h_sync_end 1480 h_blank_end 1486 h_border: 0
(II) PSB(0): v_active: 768  v_sync: 774  v_sync_end 782 v_blanking: 806 v_border: 0
(II) PSB(0):  
(II) PSB(0): Monitor name: HSD121PHW1
(II) PSB(0): EDID (in hex):
(II) PSB(0):     00ffffffffffff002264b604fe1a0000
(II) PSB(0):     05140103801b0f780a6845975a528c27
(II) PSB(0):     19505400000001010101010101010101
(II) PSB(0):     010101010101161c5678500026303042
(II) PSB(0):     68000e9610000019000000fe00000000
(II) PSB(0):     00000000000000000000000000fc0048
(II) PSB(0):     5344313231504857310a202000000010
(II) PSB(0):     000a2020202020202020202020200037
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) PSB(0): initializing int10
(II) PSB(0): Bad V_BIOS checksum
(II) PSB(0): Primary V_BIOS segment is: 0xc000
(II) PSB(0): VESA BIOS detected
(II) PSB(0): VESA VBE Version 3.0
(II) PSB(0): VESA VBE Total Mem: 7872 kB
(II) PSB(0): VESA VBE OEM: Intel(r)Poulsbo Graphics Chip Accelerated VGA BIOS
(II) PSB(0): VESA VBE OEM Software Rev: 1.0
(II) PSB(0): VESA VBE OEM Vendor: Intel Corporation
(II) PSB(0): VESA VBE OEM Product: Intel(r)Poulsbo Graphics Controller
(II) PSB(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) PSB(0): Found panel mode in BIOS VBT tables:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 (48.4 kHz)
(II) PSB(0): BLC Data in BIOS VBT tables: datasize=0 paneltype=15                      type=0x02 pol=0x00 freq=0x00c8 minlevel=0x00                         i2caddr=0x58 cmd=0xaa 
(WW) PSB(0): BIOS panel mode data doesn't match probed data, continuing with probed.
(II) PSB(0): BIOS mode:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 (48.4 kHz)
(II) PSB(0): probed mode:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) Debug: i830_psbPtrAddToList
(II) PSB(0): Debug: i830_psbSDVOInit
xf86TokenToOptinfo: table is NULL
(II) PSB(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) PSB(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) PSB(0): I2C bus "SDVOB DDC Bus" initialized.
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: sdvo_get_capabilities, caps.output_flags=3e
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Output SDVO-1 has no monitor section
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 1D                         (i830_SDVO_CMD_GET_INPUT_PIXEL_CLOCK_RANGE)
(II) PSB(0): SDVO: R: C4 09 74 40             (Success)
(II) PSB(0): SDVO device VID/DID: 02:42.02, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) Debug: i830_psbPtrAddToList
(II) Debug: i830_psbOutputCompat
(II) PSB(0): Debug: i830_psbOutputTypesToIndex
(II) PSB(0): Debug: Output crtc mask is 0x00000002, compat mask is 0x00000001
(II) PSB(0): Debug: i830_psbOutputTypesToIndex
(II) PSB(0): Debug: Output crtc mask is 0x00000001, compat mask is 0x00000002
(II) PSB(0): Debug: xxi830_psbInitCrtcs
(II) PSB(0): Debug: xxi830_psbCrtcInit
(II) PSB(0): Debug: xxi830_psbCrtcInit
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 1 as available for all screens.
(II) PSB(0): Debug: psbDeviceFinishInit
(II) Debug: Really running psbDeviceFinishInit
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Debug: xxi830_psbOutputSave
(II) PSB(0): Debug: psbLVDSSave
(II) PSB(0): Debug: xxi830_sdvo_save
(II) PSB(0): Debug: SDVO: W: 20                         (i830_SDVO_CMD_GET_CLOCK_RATE_MULT)
(II) PSB(0): SDVO: R: 01                      (Success)
(II) PSB(0): Current clock rate multiplier: 1
(II) PSB(0): Debug: SDVO: W: 04                         (i830_SDVO_CMD_GET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug:  --save_active_outputs is 0
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 12                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 13                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART2)
(II) PSB(0): SDVO: R: 00 00 00 00 16 20 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 11 00 00                   (i830_SDVO_CMD_SET_TARGET_OUTPUT)
(II) PSB(0): SDVO: R:                         (Invalid arg)
(II) PSB(0): Debug: SDVO: W: 18                         (i830_SDVO_CMD_GET_OUTPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Target not specified)
(II) PSB(0): Debug: SDVO: W: 06 00 7F 8D 64             (i830_SDVO_CMD_GET_IN_OUT_MAP)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 0.
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 1.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(**) PSB(0): Shadow framebuffer enabled
(II) Debug: i830_psbOutputAssignToScreen
(II) PSB(0): Output "SDVO-1" is assigned to this screen.
(II) Debug: i830_psbOutputAssignToScreen
(II) PSB(0): Output "LVDS0" is assigned to this screen.
(II) PSB(0): Searching for matching Poulsbo mode(s):
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID for output LVDS0
(II) PSB(0): Manufacturer: HSD  Model: 4b6  Serial#: 6910
(II) PSB(0): Year: 2010  Week: 5
(II) PSB(0): EDID Version: 1.3
(II) PSB(0): Digital Display Input
(II) PSB(0): Max Image Size [cm]: horiz.: 27  vert.: 15
(II) PSB(0): Gamma: 2.20
(II) PSB(0): No DPMS capabilities specified
(II) PSB(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) PSB(0): First detailed timing is preferred mode
(II) PSB(0): redX: 0.591 redY: 0.354   greenX: 0.322 greenY: 0.547
(II) PSB(0): blueX: 0.153 blueY: 0.098   whiteX: 0.313 whiteY: 0.329
(II) PSB(0): Manufacturer's mask: 0
(II) PSB(0): Supported detailed timing:
(II) PSB(0): clock: 71.9 MHz   Image Size:  270 x 150 mm
(II) PSB(0): h_active: 1366  h_sync: 1414  h_sync_end 1480 h_blank_end 1486 h_border: 0
(II) PSB(0): v_active: 768  v_sync: 774  v_sync_end 782 v_blanking: 806 v_border: 0
(II) PSB(0):  
(II) PSB(0): Monitor name: HSD121PHW1
(II) PSB(0): EDID (in hex):
(II) PSB(0):     00ffffffffffff002264b604fe1a0000
(II) PSB(0):     05140103801b0f780a6845975a528c27
(II) PSB(0):     19505400000001010101010101010101
(II) PSB(0):     010101010101161c5678500026303042
(II) PSB(0):     68000e9610000019000000fe00000000
(II) PSB(0):     00000000000000000000000000fc0048
(II) PSB(0):     5344313231504857310a202000000010
(II) PSB(0):     000a2020202020202020202020200037
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Printing probed modes for output LVDS0
(II) PSB(0): Modeline "1366x768"x60.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): EDID for output SDVO-1
(II) PSB(0): Output LVDS0 connected
(II) PSB(0): Output SDVO-1 disconnected
(II) PSB(0): Using exact sizes for initial modes
(II) PSB(0): Output LVDS0 using initial mode 1366x768
(II) PSB(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputDisableCrtcForOtherScreens
(II) Debug: Grabbing crtc 1 for screen 0
(**) PSB(0): Display dimensions: (270, 150) mm
(**) PSB(0): DPI set to (128, 231)
(--) Depth 24 pixmap format is 32 bpp
(II) PSB(0): Debug: psbScreenInit
(II) PSB(0): Debug: psbDRIScreenInit
(II) PSB(0): Debug: SAREA size is 8192
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "psb" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) PSB(0): [drm] Using the DRM lock SAREA also for drawables.
(II) PSB(0): [drm] framebuffer handle = 0x7f800000
(II) PSB(0): [drm] added 1 reserved context for kernel
(II) PSB(0): X context handle = 0x1
(II) PSB(0): [drm] installed DRM signal handler
(II) PSB(0): [drm] Allocated device DRM context 2.
(II) [drm] Irq handler installed for IRQ 22.
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Shadow
(II) PSB(0): Debug: Calling fbScreenInit.
(II) PSB(0): Debug: Fix up visuals.
(II) PSB(0): Debug: fbPictureInitInit
(II) PSB(0): Debug: Backing store
(==) PSB(0): Backing store disabled
(==) PSB(0): Silken mouse enabled
(==) PSB(0): DPMS enabled
(II) PSB(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) PSB(0): Debug: psbLVDSCreateResources
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: psbLVDSSetProperty  panelfitting 0
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 100
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 100(II) PSB(0): Debug: SDVO: W: 27                         (i830_SDVO_CMD_GET_SUPPORTED_TV_FORMATS)
(II) PSB(0): SDVO: R: FF FF FF FF FF 1F       (Success)
(II) PSB(0): Debug: SDVO: W: 84                         (II) PSB(0): SDVO: R: FA DF                   (Success)
(II) PSB(0): Debug: SDVO: W: 61                         (II) PSB(0): SDVO: R: 00 00 00 00             (Target not specified)
(II) PSB(0): Debug: SDVO: W: 67                         (II) PSB(0): SDVO: R: 00 00 00 00             (Target not specified)
(II) PSB(0): Debug: TVStandard is 1, TVStdBitmask is 1
(II) PSB(0): Debug: i830_sdvo_set_tvoutputs_formats, format is NTSC_M
(II) PSB(0): Debug: SDVO: W: 5A 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_hue, hue is 0
(II) PSB(0): Debug: SDVO: W: 5D 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_brightness, brightness is 0
(II) PSB(0): Debug: SDVO: W: 60 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_contrast, contrast is 0
(II) PSB(0): Debug: SDVO: W: 63 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_horzontal_overscan, x overscan is 0
(II) PSB(0): Debug: i830_sdvo_set_vertical_overscan, y overscan is 0, status is 0
(II) PSB(0): [DRI] installation complete
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Buffer 0 rotation 0 handle 0x6b980e04
(II) PSB(0): Initializing HW Cursor.
(II) PSB(0): Debug: psbEnterVT 1
(EE) PSB(0): has_fbdev is true
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Debug: xxi830_psbOutputSave
(II) PSB(0): Debug: psbLVDSSave
(II) PSB(0): Debug: xxi830_sdvo_save
(II) PSB(0): Debug: SDVO: W: 20                         (i830_SDVO_CMD_GET_CLOCK_RATE_MULT)
(II) PSB(0): SDVO: R: 01                      (Success)
(II) PSB(0): Current clock rate multiplier: 1
(II) PSB(0): Debug: SDVO: W: 04                         (i830_SDVO_CMD_GET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug:  --save_active_outputs is 0
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 12                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 13                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART2)
(II) PSB(0): SDVO: R: 00 00 00 00 16 20 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 11 00 00                   (i830_SDVO_CMD_SET_TARGET_OUTPUT)
(II) PSB(0): SDVO: R:                         (Invalid arg)
(II) PSB(0): Debug: SDVO: W: 18                         (i830_SDVO_CMD_GET_OUTPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Target not specified)
(II) PSB(0): Debug: SDVO: W: 06 00 7F 8D 64             (i830_SDVO_CMD_GET_IN_OUT_MAP)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 0.
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 1.
(II) PSB(0): Debug: psbSetVGAOff
(II) PSB(0): Debug: i830_psbCrtcSetupCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 0 ARGB addresses 0x7f800000, 0x00000000
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 1 ARGB addresses 0x7f805000, 0x00000000
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0xc0000008
(II) Debug: Pipe B PLL 0xd8020000
(II) Debug: Pipe B Enabled 0x80000000
(II) PSB(0): Debug: BLCType=2 Backlightg level = 0
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 0
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcLock
(II) PSB(0): Debug: psbLVDSModeFixup
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputDisableCrtcForOtherScreens
(II) Debug: Grabbing crtc 1 for screen 0
(II) PSB(0): Debug: xxi830_psbCrtcModeFixup, NULL
(II) PSB(0): Debug: i830_psbOutputPrepare, output->dpms,off
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0x08000001
(II) Debug: Pipe B PLL 0x58020000
(II) Debug: Pipe B Enabled 0x00000000
(II) PSB(0): Debug: BLCType=2 Backlightg level = 0
(II) PSB(0): Debug: xxi830_psbCrtcPrepare
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcModeSet
(II) PSB(0): Debug: i830_psbCrtcModeSet
(II) PSB(0): Debug: chosen: dotclock 72000 vco 2016000 ((m 105, m1 17, m2 8), n 3, (p 28, p1 2, p2 14))
(II) PSB(0): Debug: clock regs: 0xd8027200, 0x00031108
(II) PSB(0): Debug: psbPipeSetBase
(II) PSB(0): Debug: psbLVDSModeSet
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x947a070 
(II) PSB(0): Debug: xxi830_psbCrtcCommit, crtc->dpms
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS On / Sb /SS 
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x947a070 
(II) PSB(0): Debug: i830_psbOutputCommi, output->dpms, ont
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0x48000001
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) Debug: psbLVDSSetPanelPower: lidState= 0
(II) PSB(0): Debug: BLCType=2 Backlightg level = 100
(II) PSB(0): Debug: xxi830_psbCrtcUnlock
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 0
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): xxi830_Output configuration:
(II) PSB(0):   Pipe A is off
(II) PSB(0):   Display plane A is now disabled and connected to pipe A.
(II) PSB(0):   Pipe B is on
(II) PSB(0):   Display plane B is now enabled and connected to pipe B.
(II) PSB(0):   Output LVDS0 is connected to pipe B
(II) PSB(0):   Output SDVO-1 is connected to pipe none
(II) PSB(0): Debug: psbAdjustFrame
(II) PSB(0): Debug: psbPipeSetBase
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/psb_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) PSB(0): Setting screen physical size to 361 x 203
(II) PSB(0): Debug: psbXf86CrtcResize 1366 768
(II) PSB(0): Debug: i830_psbCrtcSaveCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorSave
(II) PSB(0): Debug: i830_psbCrtcHWCursorSave
(II) Debug: psbScanoutDestroy
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Buffer 0 rotation 0 handle 0x6b980e04
(II) PSB(0): Debug: i830_psbCrtcSetupCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 0 ARGB addresses 0x7fc08000, 0x00000000
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 1 ARGB addresses 0x7fc0d000, 0x00000000
(II) PSB(0): Debug: psbAdjustFrame
(II) PSB(0): Debug: psbPipeSetBase
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) XKB: reuse xkmfile /var/lib/xkb/server-188C20793BE00CBD61865C180F610EC4A3A6D8CD.xkm
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB2.0 UVC VGA WebCam (/dev/input/event6)
(**) USB2.0 UVC VGA WebCam: Applying InputClass "evdev keyboard catchall"
(**) USB2.0 UVC VGA WebCam: always reports core events
(**) USB2.0 UVC VGA WebCam: Device: "/dev/input/event6"
(II) USB2.0 UVC VGA WebCam: Found keys
(II) USB2.0 UVC VGA WebCam: Configuring as keyboard
(II) XINPUT: Adding extended input device "USB2.0 UVC VGA WebCam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device Asus EeePC extra buttons (/dev/input/event5)
(**) Asus EeePC extra buttons: Applying InputClass "evdev keyboard catchall"
(**) Asus EeePC extra buttons: always reports core events
(**) Asus EeePC extra buttons: Device: "/dev/input/event5"
(II) Asus EeePC extra buttons: Found keys
(II) Asus EeePC extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Asus EeePC extra buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) PSB(0): Debug: psbSaveScreen
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS On / Sb /SS 
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x947a070 
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0xc0000008
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) Debug: psbLVDSSetPanelPower: lidState= 0
(II) PSB(0): Debug: BLCType=2 Backlightg level = 100
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 100
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 100(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 98
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 98(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 96
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 96(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 94
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 94(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 92
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 92(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 90
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 90(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 88
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 88(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 86
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 86(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 84
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 84(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 82
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 82(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 80
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 80(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 78
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 78(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 76
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 76(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 74
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 74(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 72
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 72(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 70
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 70(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 68
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 68(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 66
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 66(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 64
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 64(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 62
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 62(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 60
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 60(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 58
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 58(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 56
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 56(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 54
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 54(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 52
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 52(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 50
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 50(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 50
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 50(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 49
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 49(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 48
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 48(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 47
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 47(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 46
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 46(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 45
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 45(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 44
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 44(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 43
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 43(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 42
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 42(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 41
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 41(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 40
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 40(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 39
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 39(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 38
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 38(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 37
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 37(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 36
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 36(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 35
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 35(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 34
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 34(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 33
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 33(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 32
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 32(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 31
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 31(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 30
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 30(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 29
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 29(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 28
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 28(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 27
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 27(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 26
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 26(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 25
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 25(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 24
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 24(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 23
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 23(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 22
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 22(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 21
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 21(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 20
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 20(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 19
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 19(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 18
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 18(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 17
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 17(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 16
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 16(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 15
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 15(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 15
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 15(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 16
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 16(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 17
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 17(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 18
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 18(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 19
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 19(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 20
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 20(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 21
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 21(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 22
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 22(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 23
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 23(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 24
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 24(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 25
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 25(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 26
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 26(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 27
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 27(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 28
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 28(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 29
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 29(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 30
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 30(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 31
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 31(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 32
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 32(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 33
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 33(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 34
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 34(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 35
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 35(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 36
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 36(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 37
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 37(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 38
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 38(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 39
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 39(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 40
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 40(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 41
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 41(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 42
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 42(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 43
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 43(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 44
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 44(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 45
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 45(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 46
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 46(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 47
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 47(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 48
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 48(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 49
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 49(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 50
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 50(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 50
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 50(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 49
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 49(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 48
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 48(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 47
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 47(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 46
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 46(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 45
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 45(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 44
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 44(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 43
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 43(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 42
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 42(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 41
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 41(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: BLCType=2 Backlightg level = 40
(II) PSB(0): Debug: psbLVDSSetProperty BLC level 40(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "HSD", prod id 1206
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Target not specified)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
```

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f650000 (usable)
[    0.000000]  BIOS-e820: 000000007f650000 - 000000007f660000 (reserved)
[    0.000000]  BIOS-e820: 000000007f660000 - 000000007f66e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f66e000 - 000000007f6b0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6b0000 - 000000007f6c0000 (reserved)
[    0.000000]  BIOS-e820: 000000007f6c8000 - 000000007f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7f650 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f650000 (usable)
[    0.000000]  modified: 000000007f650000 - 000000007f660000 (reserved)
[    0.000000]  modified: 000000007f660000 - 000000007f66e000 (ACPI data)
[    0.000000]  modified: 000000007f66e000 - 000000007f6b0000 (ACPI NVS)
[    0.000000]  modified: 000000007f6b0000 - 000000007f6c0000 (reserved)
[    0.000000]  modified: 000000007f6c8000 - 000000007f800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 3785d000 - 37fef130
[    0.000000] Allocated new RAMDISK: 008e0000 - 01072130
[    0.000000] Move RAMDISK from 000000003785d000 - 0000000037fef12f to 008e0000 - 0107212f
[    0.000000] ACPI: RSDP 000fbfd0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7f660100 00064 (v01 _ASUS_ Notebook 20100106 MSFT 00000097)
[    0.000000] ACPI: FACP 7f660290 000F4 (v04 010610 FACP1411 20100106 MSFT 00000097)
[    0.000000] ACPI: DSDT 7f660430 09642 (v02  A1451 A1451000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 7f66e000 00040
[    0.000000] ACPI: APIC 7f660390 0005C (v02 010610 APIC1411 20100106 MSFT 00000097)
[    0.000000] ACPI: MCFG 7f6603f0 0003C (v01 010610 OEMMCFG  20100106 MSFT 00000097)
[    0.000000] ACPI: OEMB 7f66e040 0012C (v01 010610 OEMB1411 20100106 MSFT 00000097)
[    0.000000] ACPI: HPET 7f669a80 00038 (v01 010610 OEMHPET  20100106 MSFT 00000097)
[    0.000000] ACPI: GSCI 7f66e170 02024 (v01 010610 GMCHSCI  20100106 MSFT 00000097)
[    0.000000] ACPI: SSDT 7f670b60 004F0 (v01  PmRef    CpuPm 00003000 INTL 20060113)
[    0.000000] ACPI: SLIC 7f669ac0 00176 (v01 _ASUS_ Notebook 20100106 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df1a8]              BRK ==> [00008dc000 - 00008df1a8]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e0000 - 0001072130]      NEW RAMDISK ==> [00008e0000 - 0001072130]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f650
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f650
[    0.000000] On node 0 totalpages: 521695
[    0.000000] free_area_init_node: node 0, pgdat c0798760, node_mem_map c1074200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292181 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f800000 (gap: 7f800000:7f600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517618
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=ff1001eb-d0ec-4253-9369-bebfb7d54ee6 ro acpi_osi=Linux acpi_backlight=vendor quiet splash
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10435840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f650)
[    0.000000] Memory: 2042448k/2087232k available (4676k kernel code, 43304k reserved, 2118k data, 660k init, 1177928k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591293 - 0xc07a2e88   (2118 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591293   (4676 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1331.279 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 2662.55 BogoMIPS (lpj=5325116)
[    0.004060] Security Framework initialized
[    0.004116] AppArmor: AppArmor initialized
[    0.004137] Mount-cache hash table entries: 512
[    0.004430] Initializing cgroup subsys ns
[    0.004443] Initializing cgroup subsys cpuacct
[    0.004455] Initializing cgroup subsys memory
[    0.004472] Initializing cgroup subsys devices
[    0.004480] Initializing cgroup subsys freezer
[    0.004486] Initializing cgroup subsys net_cls
[    0.004532] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004541] CPU: L2 cache: 512K
[    0.004548] CPU: Physical Processor ID: 0
[    0.004553] CPU: Processor Core ID: 0
[    0.004563] mce: CPU supports 5 MCE banks
[    0.004583] CPU0: Thermal monitoring enabled (TM2)
[    0.004594] using mwait in idle threads.
[    0.004609] Performance Events: Atom events, Intel PMU driver.
[    0.004632] ... version:                3
[    0.004637] ... bit width:              40
[    0.004643] ... generic registers:      2
[    0.004649] ... value mask:             000000ffffffffff
[    0.004655] ... max period:             000000007fffffff
[    0.004661] ... fixed-purpose events:   3
[    0.004667] ... event mask:             0000000700000003
[    0.004678] Checking 'hlt' instruction... OK.
[    0.020010] Disabling 4MB page tables to avoid TLB bug
[    0.025216] ACPI: Core revision 20090903
[    0.056033] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.056053] ftrace: allocating 21776 entries in 43 pages
[    0.060126] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.060457] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.102583] CPU0: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.104001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.188154] CPU1: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.188186] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.192044] Brought up 2 CPUs
[    0.192053] Total of 2 processors activated (5325.14 BogoMIPS).
[    0.192315] CPU0 attaching sched-domain:
[    0.192326]  domain 0: span 0-1 level SIBLING
[    0.192333]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.192348]   domain 1: span 0-1 level MC
[    0.192354]    groups: 0-1 (cpu_power = 1178)
[    0.192370] CPU1 attaching sched-domain:
[    0.192375]  domain 0: span 0-1 level SIBLING
[    0.192382]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.192395]   domain 1: span 0-1 level MC
[    0.192401]    groups: 0-1 (cpu_power = 1178)
[    0.192679] devtmpfs: initialized
[    0.192679] regulator: core version 0.5
[    0.192679] Time: 21:00:42  Date: 01/07/11
[    0.192679] NET: Registered protocol family 16
[    0.192679] Trying to unpack rootfs image as initramfs...
[    0.192679] EISA bus registered
[    0.192702] ACPI: bus type pci registered
[    0.192914] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.192925] PCI: Not using MMCONFIG.
[    0.193241] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.193250] PCI: Using configuration type 1 for base access
[    0.199217] bio: create slab <bio-0> at 0
[    0.203267] ACPI: EC: Look up EC in DSDT
[    0.207625] ACPI: Executed 1 blocks of module-level executable AML code
[    0.230591] ACPI: Interpreter enabled
[    0.230630] ACPI: (supports S0 S3 S4 S5)
[    0.230727] ACPI: Using IOAPIC for interrupt routing
[    0.230913] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.234804] ACPI: BIOS _OSI(Linux) query honored via cmdline
[    0.241735] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.241748] PCI: Using MMCONFIG for extended config space
[    0.265138] ACPI: EC: GPE = 0xd, I/O: command/status = 0x66, data = 0x62
[    0.265419] ACPI Warning: Incorrect checksum in table [OEMB] - F7, should be 47 (20090903/tbutils-314)
[    0.266986] ACPI: No dock devices found.
[    0.267599] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.267871] pci 0000:00:02.0: reg 10 32bit mmio: [0xf3f80000-0xf3ffffff]
[    0.267889] pci 0000:00:02.0: reg 14 io port: [0xc880-0xc887]
[    0.267905] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.267921] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf3f40000-0xf3f7ffff]
[    0.268114] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf3f38000-0xf3f3bfff]
[    0.268180] pci 0000:00:1b.0: PME# supported from D0 D3hot
[    0.268192] pci 0000:00:1b.0: PME# disabled
[    0.268291] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.268302] pci 0000:00:1c.0: PME# disabled
[    0.268401] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.268412] pci 0000:00:1c.1: PME# disabled
[    0.268489] pci 0000:00:1d.0: reg 20 io port: [0xb880-0xb89f]
[    0.268568] pci 0000:00:1d.1: reg 20 io port: [0xc080-0xc09f]
[    0.268653] pci 0000:00:1d.2: reg 20 io port: [0xc480-0xc49f]
[    0.268763] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf3f37c00-0xf3f37fff]
[    0.268861] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.268874] pci 0000:00:1d.7: PME# disabled
[    0.269012] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.269138] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfc0000-0xfbffffff]
[    0.269157] pci 0000:03:00.0: reg 18 io port: [0xe880-0xe8ff]
[    0.269248] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.269260] pci 0000:03:00.0: PME# disabled
[    0.269349] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.269361] pci 0000:00:1c.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.269459] pci 0000:01:00.0: reg 10 64bit mmio: [0xfbef0000-0xfbefffff]
[    0.269552] pci 0000:01:00.0: supports D1
[    0.269561] pci 0000:01:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.269574] pci 0000:01:00.0: PME# disabled
[    0.269671] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.269685] pci 0000:00:1c.1: bridge 32bit mmio: [0xf4000000-0xfbefffff]
[    0.269699] pci 0000:00:1c.1: bridge 32bit mmio pref: [0xcc000000-0xcfffffff]
[    0.269726] pci_bus 0000:00: on NUMA node 0
[    0.269763] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.270223] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP4._PRT]
[    0.270407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP5._PRT]
[    0.296044] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.296502] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.296967] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.297437] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.297881] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.298343] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.298783] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.299242] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.299665] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.299695] vgaarb: loaded
[    0.300192] SCSI subsystem initialized
[    0.300472] libata version 3.00 loaded.
[    0.300756] usbcore: registered new interface driver usbfs
[    0.300810] usbcore: registered new interface driver hub
[    0.300917] usbcore: registered new device driver usb
[    0.301476] ACPI: WMI: Mapper loaded
[    0.301485] PCI: Using ACPI for IRQ routing
[    0.301944] NetLabel: Initializing
[    0.301952] NetLabel:  domain hash size = 128
[    0.301959] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.301999] NetLabel:  unlabeled traffic allowed by default
[    0.302127] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.302147] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.308459] Switching to clocksource tsc
[    0.314103] AppArmor: AppArmor Filesystem Enabled
[    0.314160] pnp: PnP ACPI init
[    0.314240] ACPI: bus type pnp registered
[    0.322873] pnp: PnP ACPI: found 14 devices
[    0.322884] ACPI: ACPI bus type pnp unregistered
[    0.322897] PnPBIOS: Disabled by ACPI PNP
[    0.322949] system 00:01: iomem range 0x7f800000-0x7fffffff could not be reserved
[    0.322988] system 00:06: ioport range 0x374-0x375 has been reserved
[    0.323001] system 00:06: ioport range 0x3f4-0x3f5 has been reserved
[    0.323012] system 00:06: ioport range 0x380-0x387 has been reserved
[    0.323024] system 00:06: ioport range 0x9f4-0x9ff has been reserved
[    0.323036] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.323048] system 00:06: ioport range 0x900-0x9f3 has been reserved
[    0.323060] system 00:06: ioport range 0x400-0x43f has been reserved
[    0.323071] system 00:06: ioport range 0x480-0x4bf has been reserved
[    0.323085] system 00:06: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.323097] system 00:06: iomem range 0x384-0x387 could not be reserved
[    0.323134] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.323147] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.323171] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.323194] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.323206] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.323219] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.323231] system 00:0d: iomem range 0x100000-0x7f7fffff could not be reserved
[    0.358491] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.358506] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    0.358521] pci 0000:00:1c.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.358534] pci 0000:00:1c.0:   PREFETCH window: 0x80000000-0x801fffff
[    0.358550] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:01
[    0.358561] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.358574] pci 0000:00:1c.1:   MEM window: 0xf4000000-0xfbefffff
[    0.358586] pci 0000:00:1c.1:   PREFETCH window: 0xcc000000-0xcfffffff
[    0.358641]   alloc irq_desc for 16 on node -1
[    0.358650]   alloc kstat_irqs on node -1
[    0.358671] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.358686] pci 0000:00:1c.0: setting latency timer to 64
[    0.358707]   alloc irq_desc for 17 on node -1
[    0.358714]   alloc kstat_irqs on node -1
[    0.358729] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.358741] pci 0000:00:1c.1: setting latency timer to 64
[    0.358756] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.358767] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.358778] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.358788] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.358799] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x801fffff]
[    0.358811] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.358822] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xfbefffff]
[    0.358833] pci_bus 0000:01: resource 2 pref mem [0xcc000000-0xcfffffff]
[    0.358963] NET: Registered protocol family 2
[    0.359308] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.360433] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.361857] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.362721] TCP: Hash tables configured (established 131072 bind 65536)
[    0.362739] TCP reno registered
[    0.363074] NET: Registered protocol family 1
[    0.363141] pci 0000:00:02.0: Boot video device
[    0.363960] cpufreq-nforce2: No nForce2 chipset.
[    0.364063] Scanning for low memory corruption every 60 seconds
[    0.364454] audit: initializing netlink socket (disabled)
[    0.364487] type=2000 audit(1294434041.362:1): initialized
[    0.390735] highmem bounce pool size: 64 pages
[    0.390757] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.397055] VFS: Disk quotas dquot_6.5.2
[    0.397290] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.399810] fuse init (API version 7.13)
[    0.400174] msgmni has been set to 1690
[    0.400959] alg: No test for stdrng (krng)
[    0.401211] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.401223] io scheduler noop registered
[    0.401230] io scheduler anticipatory registered
[    0.401237] io scheduler deadline registered
[    0.401412] io scheduler cfq registered (default)
[    0.401733] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.401950] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.402167] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.402482] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.402859] ACPI: AC Adapter [AC0] (off-line)
[    0.403154] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.408559] ACPI: Lid Switch [LID]
[    0.408773] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.408786] ACPI: Sleep Button [SLPB]
[    0.408957] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.408970] ACPI: Power Button [PWRB]
[    0.411179] ACPI: SSDT 7f670270 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20060113)
[    0.413040] ACPI: SSDT 7f670500 0065D (v01  PmRef  Cpu0Cst 00003001 INTL 20060113)
[    0.415134] Monitor-Mwait will be used to enter C-1 state
[    0.415237] Monitor-Mwait will be used to enter C-2 state
[    0.415323] Monitor-Mwait will be used to enter C-3 state
[    0.415411] Monitor-Mwait will be used to enter C-3 state
[    0.416114] Marking TSC unstable due to TSC halts in idle
[    0.416266] processor LNXCPU:00: registered as cooling_device0
[    0.417238] ACPI: SSDT 7f6701a0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20060113)
[    0.418174] ACPI: SSDT 7f670470 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20060113)
[    0.420280] processor LNXCPU:01: registered as cooling_device1
[    0.427925] Switching to clocksource hpet
[    0.439494] thermal LNXTHERM:01: registered as thermal_zone0
[    0.439530] ACPI: Thermal Zone [TZ00] (45 C)
[    0.445915] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.451002] brd: module loaded
[    0.453987] loop: module loaded
[    0.454331] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.454886] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    0.456321] Fixed MDIO Bus: probed
[    0.456474] PPP generic driver version 2.4.2
[    0.456650] tun: Universal TUN/TAP device driver, 1.6
[    0.456659] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.456986] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.457059]   alloc irq_desc for 19 on node -1
[    0.457068]   alloc kstat_irqs on node -1
[    0.457089] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.457142] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.457153] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.457286] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.457357] ehci_hcd 0000:00:1d.7: debug port 1
[    0.461278] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.461363] isapnp: Scanning for PnP cards...
[    0.461428] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf3f37c00
[    0.476667] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.477038] usb usb1: configuration #1 chosen from 1 choice
[    0.477143] hub 1-0:1.0: USB hub found
[    0.477172] hub 1-0:1.0: 8 ports detected
[    0.477371] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.477426] uhci_hcd: USB Universal Host Controller Interface driver
[    0.477532]   alloc irq_desc for 20 on node -1
[    0.477540]   alloc kstat_irqs on node -1
[    0.477559] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.477578] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.477587] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.477715] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.477849] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000b880
[    0.478161] usb usb2: configuration #1 chosen from 1 choice
[    0.478259] hub 2-0:1.0: USB hub found
[    0.478283] hub 2-0:1.0: 2 ports detected
[    0.478417]   alloc irq_desc for 21 on node -1
[    0.478425]   alloc kstat_irqs on node -1
[    0.478440] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.478456] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.478466] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.478584] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.478640] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c080
[    0.478951] usb usb3: configuration #1 chosen from 1 choice
[    0.479047] hub 3-0:1.0: USB hub found
[    0.479070] hub 3-0:1.0: 2 ports detected
[    0.479201]   alloc irq_desc for 18 on node -1
[    0.479208]   alloc kstat_irqs on node -1
[    0.479222] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.479237] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.479247] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.479370] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.479425] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    0.479734] usb usb4: configuration #1 chosen from 1 choice
[    0.479829] hub 4-0:1.0: USB hub found
[    0.479852] hub 4-0:1.0: 2 ports detected
[    0.480664] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.530804] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.530830] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.536850] mice: PS/2 mouse device common for all mice
[    0.537306] rtc_cmos 00:02: RTC can wake from S4
[    0.537432] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.537538] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.537945] device-mapper: uevent: version 1.0.3
[    0.560796] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.594947] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.648282] ACPI: Battery Slot [BAT0] (battery present)
[    0.740517] device-mapper: multipath: version 1.1.0 loaded
[    0.740531] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.785142] EISA: Probing bus 0 at eisa.0
[    0.785209] EISA: Detected 0 cards.
[    0.808959] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    0.816592] isapnp: No Plug & Play device found
[    0.817323] cpuidle: using governor ladder
[    0.817891] cpuidle: using governor menu
[    0.819549] TCP cubic registered
[    0.820220] NET: Registered protocol family 10
[    0.821903] lo: Disabled Privacy Extensions
[    0.823116] NET: Registered protocol family 17
[    0.825087] Using IPI No-Shortcut mode
[    0.825422] PM: Resume from disk failed.
[    0.825479] registered taskstats version 1
[    0.826007]   Magic number: 11:682:44
[    0.826169] rtc_cmos 00:02: setting system clock to 2011-01-07 21:00:42 UTC (1294434042)
[    0.826181] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.826188] EDD information not available.
[    0.831272] Freeing initrd memory: 7752k freed
[    0.842866] Freeing unused kernel memory: 660k freed
[    0.844011] Write protecting the kernel text: 4680k
[    0.844162] Write protecting the kernel read-only data: 1840k
[    0.890543] udev: starting version 151
[    0.944699] usb 1-5: configuration #1 chosen from 1 choice
[    1.235574] pata_sch 0000:00:1f.1: version 0.2
[    1.235684] pata_sch 0000:00:1f.1: setting latency timer to 64
[    1.250324] scsi0 : pata_sch
[    1.251789] scsi1 : pata_sch
[    1.253369] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.253383] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.384291] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.466076] ata1.00: ATA-8: ST9250315AS, 0002SDM1, max UDMA/133
[    1.466094] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.481272] ata1.00: configured for UDMA/100
[    1.481685] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0002 PQ: 0 ANSI: 5
[    1.482242] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.482253] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.482477] sd 0:0:0:0: [sda] Write Protect is off
[    1.482489] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.482601] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.483226]  sda: sda1 sda2 sda3
[    1.491874] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.553467] usb 4-2: configuration #1 chosen from 1 choice
[   21.204272] udev: starting version 151
[   21.430096] lp: driver loaded but no devices found
[   21.646319] eeepc_laptop: Eee PC Hotkey Driver
[   21.647162] eeepc_laptop: Hotkey init flags 0x41
[   21.648978] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[   21.676638] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[   21.686135] eeepc_laptop: TPD (8000000) not reported by BIOS, enabling anyway
[   21.686150] eeepc_laptop: Get control methods supported: 0xe901703
[   21.730924] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input5
[   21.874785] atl1c 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.874818] atl1c 0000:03:00.0: setting latency timer to 64
[   21.968073] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   22.159080] cfg80211: Calling CRDA to update world regulatory domain
[   22.167168] ACPI: resource isch_smbus [0x400-0x43f] conflicts with ACPI region SMRG [0x400-0x43f]
[   22.167180] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.239494] Bluetooth: Core ver 2.15
[   22.243574] Linux video capture interface: v2.00
[   22.244873] NET: Registered protocol family 31
[   22.244883] Bluetooth: HCI device and connection manager initialized
[   22.244894] Bluetooth: HCI socket layer initialized
[   22.247415] cfg80211: World regulatory domain updated:
[   22.247427]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.247440]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.247451]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.247462]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.247472]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.247483]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.255112] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   22.323560] usbcore: registered new interface driver btusb
[   22.420418] uvcvideo: Found UVC 1.00 device USB2.0 UVC VGA WebCam (13d3:5111)
[   22.422365] input: USB2.0 UVC VGA WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input6
[   22.422588] usbcore: registered new interface driver uvcvideo
[   22.422601] USB Video Class driver (v0.1.0)
[   22.463989] ath9k 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.464062] ath9k 0000:01:00.0: setting latency timer to 64
[   22.513447] ath: EEPROM regdomain: 0x60
[   22.513458] ath: EEPROM indicates we should expect a direct regpair map
[   22.513472] ath: Country alpha2 being used: 00
[   22.513479] ath: Regpair used: 0x60
[   22.700097] type=1505 audit(1294434064.370:2):  operation="profile_load" pid=574 name="/sbin/dhclient3"
[   22.701059] type=1505 audit(1294434064.374:3):  operation="profile_load" pid=574 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   22.701613] type=1505 audit(1294434064.374:4):  operation="profile_load" pid=574 name="/usr/lib/connman/scripts/dhclient-script"
[   22.796471] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   22.799212] Registered led device: ath9k-phy0::radio
[   22.799290] Registered led device: ath9k-phy0::assoc
[   22.799375] Registered led device: ath9k-phy0::tx
[   22.799456] Registered led device: ath9k-phy0::rx
[   22.799523] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8340000, irq=17
[   23.151954]   alloc irq_desc for 23 on node -1
[   23.151965]   alloc kstat_irqs on node -1
[   23.151988] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   23.152730] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.253870] type=1505 audit(1294434064.926:5):  operation="profile_load" pid=712 name="/usr/share/gdm/guest-session/Xsession"
[   23.259645] type=1505 audit(1294434064.930:6):  operation="profile_replace" pid=713 name="/sbin/dhclient3"
[   23.282855] type=1505 audit(1294434064.954:7):  operation="profile_replace" pid=713 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.283425] type=1505 audit(1294434064.954:8):  operation="profile_replace" pid=713 name="/usr/lib/connman/scripts/dhclient-script"
[   23.304737] type=1505 audit(1294434064.974:9):  operation="profile_load" pid=714 name="/usr/bin/evince"
[   23.336784] type=1505 audit(1294434065.006:10):  operation="profile_load" pid=714 name="/usr/bin/evince-previewer"
[   23.342681] hda_codec: ALC269: BIOS auto-probing.
[   23.343339] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   23.345382]   alloc irq_desc for 24 on node -1
[   23.345408]   alloc kstat_irqs on node -1
[   23.345478] atl1c 0000:03:00.0: irq 24 for MSI/MSI-X
[   23.347297] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.359132] type=1505 audit(1294434065.030:11):  operation="profile_load" pid=714 name="/usr/bin/evince-thumbnailer"
[   23.467052] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.510863] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   23.608357] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
```

Muchas Gracias 
Alejandro Pernin

---

