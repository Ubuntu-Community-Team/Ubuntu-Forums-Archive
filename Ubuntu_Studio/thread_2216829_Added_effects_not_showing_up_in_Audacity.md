---
title: "Added effects not showing up in Audacity"
date: 2014-04-14
forum: Ubuntu Studio
---

### Post by shantiq on 2014-04-14
**_Quick Answer: _ **[if you do not wish to read entire thread]
Run  ```
sudo ln -s /usr/lib/ladspa /usr/share/audacity/ladspa
```


**====================================**



got Audacity and added effects on  a new install of 13.10 / also 14.04 and they are not showing up which is the first time i have seen that

i added 

> sudo apt-get install tap-plugins rev-plugins cmt liquidsoap-plugin-ladspa bs2b-ladspa invada-studio-plugins-ladspa  mcp-plugins libladspa-ocaml ladspa-foo-plugins swh-plugins libasound2-plugins   liquidsoap-plugin-all wah-plugins audacity-data swh-plugins rubberband-ladspa  zam-plugins  rubberband-vamp




and this is what it looks like

[ATTACH=CONFIG]252056[/ATTACH]


any of you been there before and know what could be missing here?    thanx in advance

---

### Post by shantiq on 2014-04-14
ok so cracked it  


looking on the Audacity site it says the plugins are here ```
[COLOR=#333333][FONT=Lucida Grande]/usr/share/audacity/plug-ins [/FONT][/COLOR]
```

and they are but only the ones with .ny extension

```
/usr/share/audacity/plug-ins$ lsadjustable-fade.ny  crossfadeout.ny  notch.ny               SoundFinder.ny
beat.ny             delay.ny         pluck.ny               StudioFadeOut.ny
clicktrack.ny       equalabel.ny     rissetdrum.ny          tremolo.ny
clipfix.ny          highpass.ny      sample-data-export.ny  vocalremover.ny
crossfadein.ny      lowpass.ny       SilenceMarker.ny       vocoder.ny



```

which is very few

so had a look for ladspa behind the scenes  ```
cd / ; find | grep -i ladspa
```


and found all these

```
./usr/lib/ladspa./usr/lib/ladspa/xfade_1915.so
./usr/lib/ladspa/gong_beater_1439.so
./usr/lib/ladspa/crossover_dist_1404.so
./usr/lib/ladspa/g2reverb.so
./usr/lib/ladspa/tap_dynamics_m.so
./usr/lib/ladspa/imp_1199.so
./usr/lib/ladspa/cmt.so
./usr/lib/ladspa/hermes_filter_1200.so
./usr/lib/ladspa/tap_eqbw.so
./usr/lib/ladspa/triple_para_1204.so
./usr/lib/ladspa/random_1661.so
./usr/lib/ladspa/delay_1898.so
./usr/lib/ladspa/tap_autopan.so
./usr/lib/ladspa/tap_doubler.so
./usr/lib/ladspa/prob_switch_2667.so
./usr/lib/ladspa/matrix_st_ms_1420.so
./usr/lib/ladspa/ringmod_1188.so
./usr/lib/ladspa/tap_tremolo.so
./usr/lib/ladspa/valve_rect_1405.so
./usr/lib/ladspa/phasers_1217.so
./usr/lib/ladspa/amp_1181.so
./usr/lib/ladspa/branch_1673.so
./usr/lib/ladspa/flanger_1191.so
./usr/lib/ladspa/tap_limiter.so
./usr/lib/ladspa/tap_deesser.so
./usr/lib/ladspa/slide_2741.so
./usr/lib/ladspa/sc2_1426.so
./usr/lib/ladspa/giant_flange_1437.so
./usr/lib/ladspa/adenv_lvl.so
./usr/lib/ladspa/tap_sigmoid.so
./usr/lib/ladspa/inv_1429.so
./usr/lib/ladspa/declip_1195.so
./usr/lib/ladspa/blvco.so
./usr/lib/ladspa/bs2b.so
./usr/lib/ladspa/dahdsr_hexp.so
./usr/lib/ladspa/fad_delay_1192.so
./usr/lib/ladspa/gverb_1216.so
./usr/lib/ladspa/hz_voct_4200.so
./usr/lib/ladspa/freq_tracker_1418.so
./usr/lib/ladspa/autotalent.so
./usr/lib/ladspa/matrix_spatialiser_1422.so
./usr/lib/ladspa/butterworth_1902.so
./usr/lib/ladspa/bode_shifter_cv_1432.so
./usr/lib/ladspa/caps.so
./usr/lib/ladspa/surround_encoder_1401.so
./usr/lib/ladspa/analogue_osc_1416.so
./usr/lib/ladspa/interpolator_1660.so
./usr/lib/ladspa/square_1643.so
./usr/lib/ladspa/quantiser100_2029.so
./usr/lib/ladspa/masher_4310.so
./usr/lib/ladspa/karaoke_1409.so
./usr/lib/ladspa/dc_remove_1207.so
./usr/lib/ladspa/plate_1423.so
./usr/lib/ladspa/sample_and_hold_4430.so
./usr/lib/ladspa/transient_1206.so
./usr/lib/ladspa/single_para_1203.so
./usr/lib/ladspa/lowpass_iir_1891.so
./usr/lib/ladspa/tape_delay_1211.so
./usr/lib/ladspa/bandpass_a_iir_1893.so
./usr/lib/ladspa/comb_1190.so
./usr/lib/ladspa/notch_iir_1894.so
./usr/lib/ladspa/csladspa.so
./usr/lib/ladspa/sync_square_1678.so
./usr/lib/ladspa/filter.so
./usr/lib/ladspa/sin_cos_1881.so
./usr/lib/ladspa/inv_filter.so
./usr/lib/ladspa/fm_osc_1415.so
./usr/lib/ladspa/tap_reflector.so
./usr/lib/ladspa/inv_input.so
./usr/lib/ladspa/delay.so
./usr/lib/ladspa/sifter_1210.so
./usr/lib/ladspa/decay_1886.so
./usr/lib/ladspa/valve_1209.so
./usr/lib/ladspa/foverdrive_1196.so
./usr/lib/ladspa/comparison_4440.so
./usr/lib/ladspa/dj_eq_1901.so
./usr/lib/ladspa/highpass_iir_1890.so
./usr/lib/ladspa/chebstortion_1430.so
./usr/lib/ladspa/vco_sawpulse.so
./usr/lib/ladspa/pulse_1645.so
./usr/lib/ladspa/multiplexer_4420.so
./usr/lib/ladspa/am_pitchshift_1433.so
./usr/lib/ladspa/tracker_2025.so
./usr/lib/ladspa/divider_1186.so
./usr/lib/ladspa/slew_limiter_2743.so
./usr/lib/ladspa/sync_pulse_2023.so
./usr/lib/ladspa/harmonic_gen_1220.so
./usr/lib/ladspa/tap_pinknoise.so
./usr/lib/ladspa/step_muxer_1212.so
./usr/lib/ladspa/ratio_2034.so
./usr/lib/ladspa/noise.so
./usr/lib/ladspa/adsr_1680.so
./usr/lib/ladspa/range_trans_4210.so
./usr/lib/ladspa/fmod_1656.so
./usr/lib/ladspa/hilbert_1440.so
./usr/lib/ladspa/tap_echo.so
./usr/lib/ladspa/decimator_1202.so
./usr/lib/ladspa/multivoice_chorus_1201.so
./usr/lib/ladspa/sawtooth_1641.so
./usr/lib/ladspa/dahdsr_2021.so
./usr/lib/ladspa/gate_1410.so
./usr/lib/ladspa/fast_crossfade_4410.so
./usr/lib/ladspa/amp_1654.so
./usr/lib/ladspa/svf_1214.so
./usr/lib/ladspa/tap_vibrato.so
./usr/lib/ladspa/sc4_1882.so
./usr/lib/ladspa/inv_compressor.so
./usr/lib/ladspa/allpass_1895.so
./usr/lib/ladspa/satan_maximiser_1408.so
./usr/lib/ladspa/adenv.so
./usr/lib/ladspa/impulse_1885.so
./usr/lib/ladspa/adsr_1653.so
./usr/lib/ladspa/sequencer16_1677.so
./usr/lib/ladspa/diode_1185.so
./usr/lib/ladspa/ladspa-rubberband.cat
./usr/lib/ladspa/sc4m_1916.so
./usr/lib/ladspa/alias_1407.so
./usr/lib/ladspa/tap_pitch.so
./usr/lib/ladspa/product_1668.so
./usr/lib/ladspa/pitch_scale_1193.so
./usr/lib/ladspa/sinus_wavewrapper_1198.so
./usr/lib/ladspa/dyson_compress_1403.so
./usr/lib/ladspa/quantiser20_2027.so
./usr/lib/ladspa/gsm_1215.so
./usr/lib/ladspa/signal_abs_2669.so
./usr/lib/ladspa/hard_limiter_1413.so
./usr/lib/ladspa/pointer_cast_1910.so
./usr/lib/ladspa/dahdsr_fexp.so
./usr/lib/ladspa/sum_1665.so
./usr/lib/ladspa/rate_shifter_1417.so
./usr/lib/ladspa/waveguide_mesh_2670.so
./usr/lib/ladspa/tap_dynamics_st.so
./usr/lib/ladspa/inv_erreverb.so
./usr/lib/ladspa/triangle_1649.so
./usr/lib/ladspa/quantiser50_2028.so
./usr/lib/ladspa/power_4400.so
./usr/lib/ladspa/bode_shifter_1431.so
./usr/lib/ladspa/latency_1914.so
./usr/lib/ladspa/comb_1887.so
./usr/lib/ladspa/dj_flanger_1438.so
./usr/lib/ladspa/tap_tubewarmth.so
./usr/lib/ladspa/foldover_1213.so
./usr/lib/ladspa/comb_splitter_1411.so
./usr/lib/ladspa/lp4pole_1671.so
./usr/lib/ladspa/difference_2030.so
./usr/lib/ladspa/sequencer32_1676.so
./usr/lib/ladspa/const_1909.so
./usr/lib/ladspa/tap_reverb.so
./usr/lib/ladspa/shaper_1187.so
./usr/lib/ladspa/fast_lookahead_limiter_1913.so
./usr/lib/ladspa/mbeq_1197.so
./usr/lib/ladspa/sine.so
./usr/lib/ladspa/gong_1424.so
./usr/lib/ladspa/autowah.so
./usr/lib/ladspa/blop_files
./usr/lib/ladspa/blop_files/square_1643_data.so
./usr/lib/ladspa/blop_files/parabola_1649_data.so
./usr/lib/ladspa/blop_files/sawtooth_1641_data.so
./usr/lib/ladspa/matrix_ms_st_1421.so
./usr/lib/ladspa/vynil_1905.so
./usr/lib/ladspa/split_1406.so
./usr/lib/ladspa/sc3_1427.so
./usr/lib/ladspa/se4_1883.so
./usr/lib/ladspa/smooth_decimate_1414.so
./usr/lib/ladspa/ladspa-rubberband.so
./usr/lib/ladspa/tap_rotspeak.so
./usr/lib/ladspa/blepvco.so
./usr/lib/ladspa/mod_delay_1419.so
./usr/lib/ladspa/inv_tube.so
./usr/lib/ladspa/sequencer64_1675.so
./usr/lib/ladspa/retro_flange_1208.so
./usr/lib/ladspa/zm1_1428.so
./usr/lib/ladspa/formant_filter_4300.so
./usr/lib/ladspa/revdelay_1605.so
./usr/lib/ladspa/tap_chorusflanger.so
./usr/lib/ladspa/delayorama_1402.so
./usr/lib/ladspa/sc1_1425.so
./usr/lib/ladspa/pitch_scale_1194.so
./usr/lib/ladspa/lcr_delay_1436.so
./usr/lib/ladspa/wave_terrain_1412.so
./usr/lib/ladspa/tap_eq.so
./usr/lib/ladspa/ls_filter_1908.so
./usr/lib/ladspa/bandpass_iir_1892.so
./usr/lib/ladspa/amp.so



```



so i copied them to Audacity plugin folder

```
cd /usr/lib/ladspa ; ls 
```  and   

```
  sudo cp * /usr/share/audacity/plug-ins 


```


and then     [ATTACH=CONFIG]252048[/ATTACH]    so better

might feasibly be of use to one of you one day :]

---

### Post by ajgreeny on 2014-04-14
You should also try the package **swh-plugins**, if it's available for 13.10.

---

### Post by shantiq on 2014-04-14
thanx aj   i had those already simply forgot to add them to the list in original post

---

### Post by angelsguitar on 2014-04-21
Thanks for the fix, shantiq.  This is also happening on 14.04, and I had to manually copy the plugins to Audacity's plugins folder.

---

### Post by Mr_Bumpy on 2014-05-18
A better solution is to symbolically link the /usr/lib/ladspa folder into /usr/share/audacity:
> sudo ln -s /usr/lib/ladspa /usr/share/audacity/ladspa
...or if you compiled your own version and installed it with the /usr/local prefix:
> sudo ln -s /usr/lib/ladspa /usr/local/share/audacity/ladspa

---

### Post by shantiq on 2014-05-18
Your route is quicker than my cumbersome way

i did not know how to create a symbolic link   Thanx for input

---

