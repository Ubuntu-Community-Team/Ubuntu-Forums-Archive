---
title: "I have errors with rtl8821ce-dkms on Pop_OS 21.04"
date: 2021-10-18
forum: Ubuntu/Debian BASED
---

### Post by GB£au17@XzMnI{BgE] on 2021-10-18
when i run the command : sudo dpkg --configure rtl8821ce-dkms
i get the following lines 
Setting up rtl8821ce-dkms (5.5.2.1-0ubuntu6) ...
Removing old rtl8821ce-5.5.2.1 DKMS files...


------------------------------
Deleting module version: 5.5.2.1
completely from the DKMS tree.
------------------------------
```
Done.
Loading new rtl8821ce-5.5.2.1 DKMS files...
Building for 5.13.0-7614-generic
Building initial module for 5.13.0-7614-generic
ERROR (dkms apport): kernel package linux-headers-5.13.0-7614-generic is not supported
Error! Bad return status for module build on kernel: 5.13.0-7614-generic (x86_64)
Consult /var/lib/dkms/rtl8821ce/5.5.2.1/build/make.log for more information.
dpkg: error processing package rtl8821ce-dkms (--configure):
 installed rtl8821ce-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 rtl8821ce-dkms
```

the error i entounter here is :
ERROR (dkms apport): kernel package linux-headers-5.13.0-7614-generic is not supported
Error! Bad return status for module build on kernel: 5.13.0-7614-generic (x86_64)

I have tried: sudo apt purge rtl8821ce-dkms 
which will give these lines.



```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  rtl8821ce-dkms*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 25.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'libpaper1:amd64' missing; assuming package has no fi
les currently installed
(Reading database ... 193981 files and directories currently installed.)
Removing rtl8821ce-dkms (5.5.2.1-0ubuntu6) ...


------------------------------
Deleting module version: 5.5.2.1
completely from the DKMS tree.
------------------------------
Done.
```

But when i install any applications from the pop shop, i get the same issue and error as above.

---

### Post by GB£au17@XzMnI{BgE] on 2021-10-18
here is the make.log file.
DKMS make.log for rtl8821ce-v5.5.2_34066.20200325 for kernel 5.13.0-7614-generic (x86_64)
```
Sun Sep 26 12:08:52 PM MSK 2021
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.13.0-7614-generic/build M=/var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build  modules
make[1]: Entering directory '/usr/src/linux-headers-5.13.0-7614-generic'
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_mi.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_chplan.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/mesh/rtw_mesh.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/mesh/rtw_mesh_pathtbl.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/mesh/rtw_mesh_hwmp.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_rson.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_btcoex_wifionly.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_beamforming.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_odm.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_rm.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_rm_fsm.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/os_intfs.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/pci_intf.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/pci_ops_linux.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/ioctl_linux.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/xmit_linux.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/mlme_linux.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/recv_linux.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/rtw_cfgvendor.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/wifi_regd.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/rtw_android.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/rtw_proc.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/rtw_rhashtable.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/os_dep/linux/ioctl_mp.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_intf.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_com.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_com_phycfg.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_phy.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_dm.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_dm_acs.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_btcoex_wifionly.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_btcoex.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_mp.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_mcc.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_hci/hal_pci.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/led/hal_led.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/led/hal_pci_led.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/rtl8821c_halinit.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/rtl8821c_mac.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/rtl8821c_cmd.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/rtl8821c_phy.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/rtl8821c_dm.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/rtl8821c_ops.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/hal8821c_fw.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/pci/rtl8821ce_halinit.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/pci/rtl8821ce_halmac.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/pci/rtl8821ce_io.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/pci/rtl8821ce_xmit.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/pci/rtl8821ce_recv.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/pci/rtl8821ce_led.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/rtl8821c/pci/rtl8821ce_ops.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/efuse/rtl8821c/HalEfuseMask8821C_PCIE.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_halmac.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_api.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_bb_rf_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_cfg_wmac_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_common_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_efuse_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_flash_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_fw_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_gpio_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_init_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_mimo_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_pcie_88xx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_8821c/halmac_cfg_wmac_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_8821c/halmac_common_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_8821c/halmac_gpio_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_8821c/halmac_init_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_8821c/halmac_phy_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_8821c/halmac_pwr_seq_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build//hal/halmac/halmac_88xx/halmac_8821c/halmac_pcie_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_debug.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_antdiv.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_soml.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_smt_ant.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_antdect.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_interface.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_phystatus.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_hwconfig.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_dig.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_pathdiv.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_rainfo.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_dynamictxpower.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_adaptivity.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_cfotracking.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_noisemonitor.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_beamforming.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_dfs.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/txbf/halcomtxbf.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/txbf/haltxbfinterface.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/txbf/phydm_hal_txbf_api.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_adc_sampling.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_ccx.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_psd.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_primary_cca.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_cck_pd.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_rssi_monitor.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_auto_dbg.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_math_lib.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_api.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_pow_train.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_lna_sat.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_pmac_tx_setting.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/phydm_mp.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/halrf.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/halrf_debug.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/halphyrf_ce.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/halrf_powertracking_ce.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/halrf_powertracking.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/halrf_kfree.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/rtl8821c/halhwimg8821c_bb.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/rtl8821c/halhwimg8821c_mac.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/rtl8821c/halhwimg8821c_rf.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/rtl8821c/phydm_hal_api8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/rtl8821c/phydm_regconfig8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/rtl8821c/halrf_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/phydm/halrf/rtl8821c/halrf_iqk_8821c.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/btc/halbtc8821cwifionly.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/btc/halbtc8821c1ant.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/btc/halbtc8821c2ant.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/platform/platform_ops.o
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/core/rtw_mp.o
  LD [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/8821ce.o
  MODPOST /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/Module.symvers
  CC [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/8821ce.mod.o
  LD [M]  /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/8821ce.ko
  BTF [M] /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/8821ce.ko
Skipping BTF generation for /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/8821ce.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-7614-generic'
```

---

### Post by lord-harald-blackwolf on 2021-10-27
Hi, I am reciving the same error. Did you find a fix?

---

### Post by jeremy31 on 2021-10-27
Try something like this?
```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh
```

---

