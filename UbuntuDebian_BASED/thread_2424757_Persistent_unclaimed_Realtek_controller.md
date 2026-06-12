---
title: "Persistent unclaimed Realtek controller"
date: 2019-08-14
forum: Ubuntu/Debian BASED
---

### Post by MibunoOokami on 2019-08-14
Hi all  To keep this short. I upgraded to 19.04 a couple of months ago, built-in wifi wasn’t detected, used USB adaptor instead.  A couple of days ago, decided to give Zorin a try, it too wouldn’t detect wifi.  Searching for solutions suggested: ```
sudo lshw -C network
```  To see if the adaptor is detected. The result: ```
*-network UNCLAIMED             description: Network controller        product: RTL8821CE 802.11ac PCIe Wireless Network Adapter        vendor: Realtek Semiconductor Co., Ltd.        physical id: 0        bus info: pci@0000:01:00.0        version: 00        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress cap_list        configuration: latency=0        resources: ioport:e000(size=256) memory:fea00000-fea0ffff
```  Searching for help regarding unclaimed controllers, yielded some potential solutions:  One theory was that drivers couldn’t be installed because secure boot was enabled, solution, disable. This was not my case as it had remained disabled, I checked before starting install.  Another solution was to purge the bcmwl-kernel-source and reinstall it. This didn’t work  Next was ```
sudo -i echo "options rtl8821ce msi=1"  >  /etc/modprobe.d/rtl8821ce.conf exit
``` Didn’t work  Thinking this might be Zorin specific, I gave Ubuntu-Mate a quick spin. Same problem, same ineffective solutions. Decided to be smart and did a fresh install of Windows thinking that might somehow fix the issue. Nope. Finally I tried resetting all the BIOS defaults to factory fresh... Still nothing. Needless to say, the suggestions and confirmed solutions of doing a fresh install didn’t work either.  Sorry it’s not as short as I hoped. Given that this problem on multiple forums/blogs seems to get very little response (as in someone will start a thread a long time ago, but no responses are given), and the solutions which are offered seem to help everyone else, I’m wondering if it’s even worth asking this question, but... Can anyone tell me why I seem to have a persistently unclaimed, and seemingly un-claimable Realtek controller? And how I can reclaim it please?  P.S I'm back using a fresh install of Zorin, if that matters. Edit: No additional drivers available in any of the versions when I checked.

---

### Post by chili555 on 2019-08-14
Please try this: [https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258](https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258)

---

### Post by howefield on 2019-08-14
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by MibunoOokami on 2019-08-16
> **chili555 said:**
> Please try this: [https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258](https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258)

Just tried that, but was unsuccessful, the device is still unclaimed and not detected.

---

### Post by chili555 on 2019-08-16
What is the exact response to the terminal command:```
sudo modprobe 8821ce
```

---

### Post by MibunoOokami on 2019-08-17
> **chili555 said:**
> What is the exact response to the terminal command:```
sudo modprobe 8821ce
```

No output...

---

### Post by chili555 on 2019-08-17
> **MibunoOokami said:**
> No output...

Let’s have a look at:```
lspci  -nnk | grep 0280
modinfo 8821ce
```

---

### Post by MibunoOokami on 2019-08-17
```
lspci  -nnk | grep 0280
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]

```

```
modinfo 8821ce
filename:       /lib/modules/4.15.0-30-generic/updates/dkms/8821ce.ko
version:        v5.5.2_34066.20190614_COEX20180712-3232
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     0FAAE8BA985C1EE690CE616
alias:          pci:v000010ECd0000C82Bsv*sd*bc*sc*i*
alias:          pci:v000010ECd0000C82Asv*sd*bc*sc*i*
alias:          pci:v000010ECd0000C821sv*sd*bc*sc*i*
depends:        cfg80211
retpoline:      Y
name:           8821ce
vermagic:       4.15.0-30-generic SMP mod_unload 
parm:           rtw_wireless_mode:int
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_lps_level:The default LPS level (int)
parm:           rtw_lps_chk_by_tp:int
parm:           rtw_max_bss_cnt:int
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_dynamic_agg_enable:int
parm:           rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
parm:           rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
parm:           rtw_rx_ampdu_sz_limit_1ss:RX AMPDU size limit for 1SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_2ss:RX AMPDU size limit for 2SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_3ss:RX AMPDU size limit for 3SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_4ss:RX AMPDU size limit for 4SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_vht_enable:int
parm:           rtw_vht_rx_mcs_map:VHT RX MCS map (uint)
parm:           rtw_rf_config:int
parm:           rtw_country_code:The default country code (in alpha2) (charp)
parm:           rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
parm:           rtw_excl_chs:exclusive channel array (array of uint)
parm:           rtw_btcoex_enable:BT co-existence on/off, 0:off, 1:on, 2:by efuse (int)
parm:           rtw_ant_num:Antenna number setting, 0:by efuse (int)
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_pwrtrim_enable:int
parm:           rtw_initmac:charp
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_uapsd_max_sp:int
parm:           rtw_uapsd_ac_enable:int
parm:           rtw_wmm_smart_ps:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_rx_ampdu_amsdu:int
parm:           rtw_tx_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_full_ch_in_p2p_handshake:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_drv_ant_band_switch:int
parm:           rtw_single_ant_path:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_check_hw_status:int
parm:           rtw_pci_aspm_enable:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_th_l2h_ini:th_l2h_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:th_edcca_hl_diff for Adaptivity (int)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_powertracking_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gh:uint
parm:           rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_a:5G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_b:5G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_c:5G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_d:5G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_tsf_update_pause_factor:num of bcn intervals to stay TSF update pause status (int)
parm:           rtw_tsf_update_restore_factor:num of bcn intervals to stay TSF update restore status (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
parm:           rtw_en_napi:int
parm:           rtw_en_gro:int
parm:           rtw_iqk_fw_offload:int
parm:           rtw_ch_switch_offload:int

```

---

### Post by chili555 on 2019-08-17
> 
Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [[COLOR="#FF0000"]10ec:c821[/COLOR]]
The driver covers your exact device:> 
modinfo 8821ce
filename:       /lib/modules/4.15.0-30-generic/updates/dkms/8821ce.ko
version:        v5.5.2_34066.20190614_COEX20180712-3232
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     0FAAE8BA985C1EE690CE616
alias:          pci:v000010ECd0000C82Bsv*sd*bc*sc*i*
alias:          pci:v000010ECd0000C82Asv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]10EC[/COLOR]d0000[COLOR="#FF0000"]C821[/COLOR]sv*sd*bc*sc*i*

So I don't understand what is meant by:> ust tried that, but was unsuccessful

Let's see:```
rfkill list all
dmesg | grep -i rtl
dmesg | grep 8821
iwconfig
```

---

### Post by MibunoOokami on 2019-08-17
Perhaps I used the wrong choice of words. What was meant is that because the internal wi-fi adapter is still not being detected, and is still showing up as unclaimed, the commands must have been unsuccessful.

```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```
dmesg | grep -i rtl
[    1.253526] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0x        (ptrval), 98:29:a6:92:0c:ea, XID 0c000880 IRQ 32
[    1.820088] usb 2-2: Product: RTL8191S WLAN Adapter 
[   19.182090] RTW: rtl8821ce v5.5.2_34066.20190614_COEX20180712-3232
[   19.182092] RTW: rtl8821ce BT-Coex version = COEX20180712-3232
[   19.183728] rtl8821ce 0000:01:00.0: enabling device (0000 -> 0003)
[   19.187187] RTW: CHIP TYPE: RTL8821CE
[   19.231879] rtl8821ce 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0001 address=0x00000000ffff3000 flags=0x0000]
[   20.195245] r8712u: register rtl8712_netdev_ops to netdev_ops
[   21.334847] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   29.404262] RTW: ERROR rtl8821c_fw_dl Download Firmware from array failed

```

```
dmesg | grep 8821
[   19.182090] RTW: rtl8821ce v5.5.2_34066.20190614_COEX20180712-3232
[   19.182092] RTW: rtl8821ce BT-Coex version = COEX20180712-3232
[   19.183728] rtl8821ce 0000:01:00.0: enabling device (0000 -> 0003)
[   19.187187] RTW: CHIP TYPE: RTL8821CE
[   19.188594] RTW: Chip Version Info: CHIP_8821C_Normal_Chip_UMC_B_CUT_1T1R_RomVer(1)
[   19.231879] rtl8821ce 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0001 address=0x00000000ffff3000 flags=0x0000]
[   29.404262] RTW: ERROR rtl8821c_fw_dl Download Firmware from array failed

```

```
iwconfig
lo        no wireless extensions.

enp2s0    no wireless extensions.


```

---

### Post by chili555 on 2019-08-18
> 
[   21.334847] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   29.404262] RTW: ERROR rtl8821c_fw_dl Download Firmware from array failed
Ah, haaaa! 

Do you actually have the firmware file and with the right permissions?```

ls -al /lib/firmware/rtlwifi | grep 8712
```Ideally, we'd like to see:```

-rw-r--r--  1 root  root  122328 Mar 29  2017 rtl8712u.bin
```

---

### Post by MibunoOokami on 2019-08-18
Yes, it looks the same except for the date

```
ls -al /lib/firmware/rtlwifi | grep 8712
-rw-r--r--  1 root root 122328 Mar 30  2017 rtl8712u.bin

```

Edit: The USB wi-fi adapter wouldn't be making a mess of things would it? I'm just wondering with the right driver being there, and with the correct permissions etc, if that might be having some unintended effect.

---

### Post by MibunoOokami on 2019-08-20
This is totally bizarre, the internet connection randomly dropped today and was unable to connect for several minutes, then the notice appeared saying there are wifi networks available and to select one. Checked it out and there was a double up of all available networks due to the internal wifi adapter suddenly working.
 
 
 I wasn’t doing anything on the PC at the time, just happened look up and see the disconnected internet connection, then the notification, so I’m completely clueless as to how the internal Realtek controller has started to work, especially after so many days since following your instructions. Saved me having to spend time moving the machine within reach of an ethernet cable to try re-installing the driver so that’s a bonus.
 
 
 Thanks for your help in solving this, it’s much appreciated.

---

