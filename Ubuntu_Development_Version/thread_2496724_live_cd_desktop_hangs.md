---
title: "live cd desktop hangs"
date: 2024-04-09
forum: Ubuntu Development Version
---

### Post by makitso on 2024-04-09
I have a Thinkpad T510 that is running an old install of Ubuntu Budgie 24.04.  after the .iso issues last week I thought I would reinstall the latest download.\

Booting the livecd, I notice that instead of the nice desktop graphics for Budgie I get a text line saying Ubuntu Budgie 24.04.
Then when the desktop finally loads the liveCD locks up tight.  Only a hard reset works.

I tried a couple of kernel boot parameters, [FONT=Arial]intel_iommu=off and nomodeset but nothing helps.
[/FONT]Suggestions?

```

$ inxi -FZRa
System:
  Host: rob-ThinkPad-T510 Kernel: 6.8.0-11-generic arch: x86_64 bits: 64
    compiler: gcc v: 13.2.0 clocksource: tsc avail: hpet,acpi_pm
    parameters: BOOT_IMAGE=/boot/vmlinuz-6.8.0-11-generic
    root=UUID=35c54a5b-4746-419b-a598-d3d408c9066a ro quiet splash
    vt.handoff=7
  Desktop: Budgie v: 10.9.1 tk: GTK v: 3.24.41 wm: budgie-wm
    with: budgie-panel,plank tools: gnome-screensaver,gsd-screensaver-proxy
    dm: LightDM v: 1.30.0 Distro: Budgie 24.04 LTS (Noble Numbat) base: Ubuntu
Machine:
  Type: Laptop System: LENOVO product: 4384AJ9 v: ThinkPad T510
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: LENOVO model: 4384AJ9 serial: <superuser required>
    uuid: <superuser required> BIOS: LENOVO v: 6MET92WW (1.52 ) date: 09/26/2012
Battery:
  ID-1: BAT0 charge: 47.8 Wh (97.8%) condition: 48.9/47.5 Wh (103.0%)
    volts: 11.7 min: 10.8 model: LGC 42T4848 type: Li-ion serial: 39414
    status: discharging
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M325
    serial: 22-c2-4c-cc charge: 55% (should be ignored) rechargeable: yes
    status: discharging
CPU:
  Info: model: Intel Core i7 M 620 bits: 64 type: MT MCP arch: Westmere
    gen: core 1 level: v2 built: 2010-11 process: Intel 32nm family: 6
    model-id: 0x25 (37) stepping: 2 microcode: 0x11
  Topology: cpus: 1x cores: 2 tpc: 2 threads: 4 smt: enabled cache:
    L1: 128 KiB desc: d-2x32 KiB; i-2x32 KiB L2: 512 KiB desc: 2x256 KiB
    L3: 4 MiB desc: 1x4 MiB
  Speed (MHz): avg: 1720 high: 2667 min/max: 1199/2667 boost: enabled
    scaling: driver: acpi-cpufreq governor: schedutil cores: 1: 1199 2: 2667
    3: 1553 4: 1463 bogomips: 21280
  Flags: ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
  Vulnerabilities:
  Type: gather_data_sampling status: Not affected
  Type: itlb_multihit status: KVM: VMX disabled
  Type: l1tf mitigation: PTE Inversion; VMX: conditional cache flushes, SMT
    vulnerable
  Type: mds status: Vulnerable: Clear CPU buffers attempted, no microcode;
    SMT vulnerable
  Type: meltdown mitigation: PTI
  Type: mmio_stale_data status: Unknown: No mitigations
  Type: retbleed status: Not affected
  Type: spec_rstack_overflow status: Not affected
  Type: spec_store_bypass mitigation: Speculative Store Bypass disabled via
    prctl
  Type: spectre_v1 mitigation: usercopy/swapgs barriers and __user pointer
    sanitization
  Type: spectre_v2 mitigation: Retpolines, IBPB: conditional, IBRS_FW,
    STIBP: conditional, RSB filling, PBRSB-eIBRS: Not affected
  Type: srbds status: Not affected
  Type: tsx_async_abort status: Not affected
Graphics:
  Device-1: Intel Core Processor Integrated Graphics vendor: Lenovo
    driver: i915 v: kernel arch: Gen-5.75 process: Intel 45nm built: 2010 ports:
    active: LVDS-1 empty: DP-1, DP-2, DP-3, HDMI-A-1, HDMI-A-2, HDMI-A-3,
    VGA-1 bus-ID: 00:02.0 chip-ID: 8086:0046 class-ID: 0300
  Display: x11 server: X.Org v: 21.1.11 compositor: budgie-wm driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: crocus gpu: i915
    display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1366x768 s-dpi: 96 s-size: 361x203mm (14.21x7.99")
    s-diag: 414mm (16.31")
  Monitor-1: LVDS-1 model: Lenovo 0x40b0 built: 2010 res: 1366x768 hz: 60
    dpi: 101 gamma: 1.2 size: 345x194mm (13.58x7.64") diag: 396mm (15.6")
    ratio: 16:9 modes: 1366x768
  API: EGL v: 1.5 hw: drv: intel crocus platforms: device: 0 drv: crocus
    device: 1 drv: swrast surfaceless: drv: crocus x11: drv: crocus
    inactive: gbm,wayland
  API: OpenGL v: 4.5 compat-v: 2.1 vendor: intel mesa v: 24.0.3-1ubuntu3
    glx-v: 1.4 direct-render: yes renderer: Mesa Intel HD Graphics (ILK)
    device-ID: 8086:0046 memory: 1.46 GiB unified: yes
Audio:
  Device-1: Intel 5 Series/3400 Series High Definition Audio vendor: Lenovo 5
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0 chip-ID: 8086:3b56
    class-ID: 0403
  API: ALSA v: k6.8.0-11-generic status: kernel-api
    tools: alsactl,alsamixer,amixer
  Server-1: PipeWire v: 1.0.4 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
    tools: pw-cat,pw-cli,wpctl
Network:
  Device-1: Intel 82577LM Gigabit Network vendor: Lenovo driver: e1000e
    v: kernel port: 1820 bus-ID: 00:19.0 chip-ID: 8086:10ea class-ID: 0200
  IF: enp0s25 state: down mac: f0:de:f1:4c:d3:b9
  Device-2: Intel Centrino Advanced-N 6200 driver: iwlwifi v: kernel pcie:
    gen: 1 speed: 2.5 GT/s lanes: 1 bus-ID: 03:00.0 chip-ID: 8086:4239
    class-ID: 0280
  IF: wlp3s0 state: up mac: 58:94:6b:79:73:d4
  Info: services: NetworkManager, smbd, systemd-timesyncd, wpa_supplicant
RAID:
  Message: No RAID data found.
Drives:
  Local Storage: total: 238.47 GiB used: 11.89 GiB (5.0%)
  SMART Message: Unable to run smartctl. Root privileges required.
  ID-1: /dev/sda maj-min: 8:0 vendor: SanDisk model: SD7UB3Q256G1001
    size: 238.47 GiB block-size: physical: 512 B logical: 512 B speed: 3.0 Gb/s
    tech: SSD serial: 151084402176 fw-rev: 0501 scheme: MBR
Partition:
  ID-1: / raw-size: 19.53 GiB size: 19.06 GiB (97.57%) used: 11.32 GiB (59.4%)
    fs: ext4 dev: /dev/sda6 maj-min: 8:6
  ID-2: /home raw-size: 23.64 GiB size: 23.11 GiB (97.72%)
    used: 574.8 MiB (2.4%) fs: ext4 dev: /dev/sda8 maj-min: 8:8
Swap:
  Kernel: swappiness: 60 (default) cache-pressure: 100 (default) zswap: no
  ID-1: swap-1 type: file size: 3.33 GiB used: 0 KiB (0.0%) priority: -2
    file: /swap.img
Sensors:
  System Temperatures: cpu: 37.0 C mobo: N/A
  Fan Speeds (rpm): fan-1: 2608
Info:
  Memory: total: 4 GiB note: est. available: 3.63 GiB used: 1.45 GiB (40.1%)
  Processes: 267 Power: uptime: 3m states: freeze,mem,disk suspend: deep
    avail: s2idle wakeups: 0 hibernate: platform avail: shutdown, reboot,
    suspend, test_resume image: 1.42 GiB services: gsd-power,upowerd
    Init: systemd v: 255 target: graphical (5) default: graphical
    tool: systemctl
  Packages: 2284 pm: dpkg pkgs: 2273 libs: 1254 tools: apt, apt-get,
    gnome-software, synaptic pm: snap pkgs: 11 Compilers: gcc: 13.2.0
    Shell: Bash v: 5.2.21 running-in: gnome-terminal inxi: 3.3.33

```

---

### Post by makitso on 2024-04-09
I suspect that the wrong or no video drivers were loaded by the lived.  Any way to fix this at boot time?

---

### Post by makitso on 2024-04-15
The problem may be the new Intel Arc drivers.

---

### Post by makitso on 2024-04-29
This problem is a 6.8 kernal issue.  I installed the 6.7 kernal in release 24.04 and it worked fine.

---

