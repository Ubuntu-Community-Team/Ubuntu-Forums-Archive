---
title: "a 2003 version of wine to compile to use VST server :P"
date: 2009-09-18
forum: Wine
---

### Post by dead_devil_66 on 2009-09-18
(NOTE: Using Ubuntu Studio 9.04)

Hey guys!

I need a hand in here...

[http://quicktoots.linuxaudio.org/toots/vst-plugins/](http://quicktoots.linuxaudio.org/toots/vst-plugins/)

in this page, the author wrote that the best WINE version to use with vst server is the one in here:

[http://www.notam02.no/arkiv/src/](http://www.notam02.no/arkiv/src/)

I downloaded both WINE and VSTServer packages in that page. Next, i ran "./configure" in the console and everything went all nice (as far as i can see). After that, i ran "make depend && make" and it ended up in error. See the following code:

```

cd `dirname dlls/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/dlls'
cd `dirname advapi32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/advapi32'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/advapi32/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. registry.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/advapi32/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. advapi.c crypt.c eventlog.c registry.c security.c service.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/advapi32'
cd `dirname avicap32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/avicap32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. avicap32_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/avicap32'
cd `dirname avifil32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/avifil32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. acmstream.c api.c avifile.c editstream.c extrachunk.c factory.c getframe.c icmstream.c regsvr.c tmpfile.c wavfile.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/avifil32'
cd `dirname cabinet/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/cabinet'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cabextract.c cabinet_main.c fci.c fdi.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/cabinet'
cd `dirname capi2032/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/capi2032'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cap20wxx.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/capi2032'
cd `dirname cfgmgr32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/cfgmgr32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/cfgmgr32'
cd `dirname comcat/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/comcat'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. comcat_main.c factory.c information.c manager.c register.c regsvr.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/comcat'
cd `dirname comctl32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/comctl32'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/comctl32/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. dpa.c tab.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/comctl32/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. animate.c comboex.c comctl32undoc.c commctrl.c datetime.c draglist.c flatsb.c header.c hotkey.c imagelist.c ipaddress.c listview.c monthcal.c nativefont.c pager.c progress.c propsheet.c rebar.c smoothscroll.c status.c tab.c toolbar.c tooltips.c trackbar.c treeview.c updown.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/comctl32'
cd `dirname commdlg/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/commdlg'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cdlg32.c colordlg.c filedlg.c filedlgbrowser.c finddlg32.c filetitle.c fontdlg.c generic.c printdlg.c colordlg16.c filedlg16.c finddlg.c fontdlg16.c printdlg16.c rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/commdlg'
cd `dirname crtdll/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/crtdll'
../../tools/makedep -I. -I. -I../../include -I../../include -I../../include/msvcrt -C. crtdll_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/crtdll'
cd `dirname crypt32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/crypt32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/crypt32'
cd `dirname ctl3d/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/ctl3d'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. ctl3d32.c ctl3d.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/ctl3d'
cd `dirname d3dim/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/d3dim'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. d3dim_main.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/d3dim'
cd `dirname dciman32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dciman32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dciman_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dciman32'
cd `dirname devenum/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/devenum'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. createdevenum.c devenum_main.c factory.c mediacatenum.c parsedisplayname.c  devenum.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/devenum'
cd `dirname dinput/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dinput'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. device.c dinput_main.c joystick/linux.c joystick/linuxinput.c keyboard/main.c mouse/main.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dinput'
cd `dirname dinput8/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dinput8'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dinput8_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dinput8'
cd `dirname dmband/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmband'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. band.c bandtrack.c dmband_main.c regsvr.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmband'
cd `dirname dmcompos/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmcompos'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. chordmap.c chordmaptrack.c composer.c dmcompos_main.c regsvr.c signposttrack.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmcompos'
cd `dirname dmime/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmime'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. audiopath.c dmime_main.c graph.c lyricstrack.c markertrack.c paramcontroltrack.c patterntrack.c performance.c regsvr.c segment.c segmentstate.c segtriggertrack.c seqtrack.c song.c sysextrack.c tempotrack.c timesigtrack.c tool.c wavetrack.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmime'
cd `dirname dmloader/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmloader'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. container.c dmloader_main.c loader.c loaderstream.c regsvr.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmloader'
cd `dirname dmscript/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmscript'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dmscript_main.c regsvr.c script.c scripttrack.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmscript'
cd `dirname dmstyle/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmstyle'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. auditiontrack.c chordtrack.c commandtrack.c dmstyle_main.c melodyformulationtrack.c motiftrack.c mutetrack.c regsvr.c style.c styletrack.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmstyle'
cd `dirname dmsynth/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmsynth'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dmsynth_main.c regsvr.c synth.c synthsink.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmsynth'
cd `dirname dmusic/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmusic'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. buffer.c clock.c collection.c dmusic.c dmusic_main.c download.c downloadedinstrument.c instrument.c port.c portdownload.c regsvr.c thru.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmusic'
cd `dirname dmusic32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dmusic32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dmusic32_main.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dmusic32'
cd `dirname dplay/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dplay'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dplay_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dplay'
cd `dirname dplayx/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dplayx'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dpclassfactory.c dplay.c dplaysp.c dplayx_global.c dplayx_main.c dplayx_messages.c dplobby.c lobbysp.c name_server.c regsvr.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dplayx'
cd `dirname dpnhpast/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dpnhpast'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dpnhpast'
cd `dirname dsound/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/dsound'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/dsound/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. capture.c dsound.c propset.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/dsound/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. buffer.c capture.c dsound_main.c mixer.c primary.c propset.c regsvr.c sound3d.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/dsound'
cd `dirname gdi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/gdi'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/gdi/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. generated.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/gdi/tests'
../../tools/makedep -I. -I. -I../../include -I../../include -I/usr/include/freetype2 -C. ../../graphics/bitblt.c ../../graphics/dispdib.c ../../graphics/env.c ../../graphics/escape.c ../../graphics/fontengine.c ../../graphics/mapping.c ../../graphics/painting.c ../../graphics/path.c ../../objects/bitmap.c ../../objects/brush.c ../../objects/clipping.c ../../objects/dc.c ../../objects/dcvalues.c ../../objects/dib.c ../../objects/enhmetafile.c ../../objects/font.c ../../objects/gdiobj.c ../../objects/linedda.c ../../objects/metafile.c ../../objects/palette.c ../../objects/pen.c ../../objects/region.c ../../objects/text.c bidi.c driver.c enhmfdrv/bitblt.c enhmfdrv/dc.c enhmfdrv/graphics.c enhmfdrv/init.c enhmfdrv/mapping.c enhmfdrv/objects.c freetype.c gdi_main.c mfdrv/bitblt.c mfdrv/dc.c mfdrv/graphics.c mfdrv/init.c mfdrv/mapping.c mfdrv/objects.c mfdrv/text.c printdrv.c bidi16.c gdi16.c wing.c version.rc version16.rc   
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/gdi'
cd `dirname icmp/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/icmp'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. icmp_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/icmp'
cd `dirname imagehlp/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/imagehlp'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. access.c debug.c imagehlp_main.c integrity.c internal.c modify.c symbol.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/imagehlp'
cd `dirname imm32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/imm32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. imm.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/imm32'
cd `dirname iphlpapi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/iphlpapi'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. ifenum.c iphlpapi_main.c ipstats.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/iphlpapi'
cd `dirname kernel/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/kernel'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/kernel/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. alloc.c atom.c codepage.c comm.c console.c directory.c drive.c environ.c file.c format_msg.c generated.c heap.c locale.c mailslot.c path.c pipe.c process.c profile.c thread.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/kernel/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. ../../files/directory.c ../../files/dos_fs.c ../../files/drive.c ../../files/file.c ../../files/smb.c ../../misc/options.c ../../misc/registry.c atom.c change.c comm.c computername.c console.c cpu.c debugger.c device.c dosmem.c editline.c environ.c except.c fiber.c file.c file16.c format_msg.c global16.c heap.c instr.c kernel_main.c lcformat.c local16.c locale.c module.c ne_module.c ne_segment.c powermgnt.c process.c profile.c pthread.c relay16.c resource.c resource16.c selector.c snoop16.c stress.c string.c sync.c syslevel.c system.c tape.c task.c thread.c thunk.c time.c toolhelp.c utthunk.c version.c virtual.c vxd.c win87em.c windebug.c wowthunk.c error16.c registry16.c kernel.rc version16.rc messages/winerr_enu.mc  
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/kernel'
cd `dirname lzexpand/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/lzexpand'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. lzexpand_main.c lzexpand16.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/lzexpand'
cd `dirname mapi32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/mapi32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. mapi32_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/mapi32'
cd `dirname mpr/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/mpr'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. auth.c mpr_main.c multinet.c nps.c pwcache.c wnet.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/mpr'
cd `dirname msacm/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msacm'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. driver.c filter.c format.c internal.c msacm32_main.c pcmconverter.c stream.c msacm_main.c msacm.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msacm'
cd `dirname msacm/imaadp32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msacm/imaadp32'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. imaadp32.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msacm/imaadp32'
cd `dirname msacm/msadp32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msacm/msadp32'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. msadp32.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msacm/msadp32'
cd `dirname msacm/msg711/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msacm/msg711'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. msg711.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msacm/msg711'
cd `dirname msacm/winemp3/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msacm/winemp3'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. common.c dct64_i386.c decode_i386.c interface.c layer1.c layer2.c layer3.c mpegl3.c tabinit.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msacm/winemp3'
cd `dirname msdmo/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msdmo'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dmoreg.c dmort.c msdmo_main.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msdmo'
cd `dirname mshtml/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/mshtml'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. document.c main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/mshtml'
cd `dirname msi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msi'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. distinct.c handle.c msi.c msiquery.c order.c record.c select.c suminfo.c table.c tokenize.c where.c      sql.y 
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msi'
cd `dirname msimg32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msimg32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. msimg32_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msimg32'
cd `dirname msisys/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msisys'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. msisys.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msisys'
cd `dirname msnet32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msnet32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. msnet_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msnet32'
cd `dirname msvcrt/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msvcrt'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/msvcrt/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include -I../../../include/msvcrt -C. cpp.c file.c heap.c scanf.c       testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/msvcrt/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. console.c cpp.c cppexcept.c ctype.c data.c dir.c environ.c errno.c except.c exit.c file.c heap.c lconv.c locale.c lock.c main.c math.c mbcs.c misc.c process.c scanf.c string.c thread.c time.c wcs.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msvcrt'
cd `dirname msvcrt20/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msvcrt20'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. msvcrt20.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msvcrt20'
cd `dirname msvcrtd/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msvcrtd'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. debug.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msvcrtd'
cd `dirname msvideo/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msvideo'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. mciwnd.c msvideo_main.c drawdib.c msvideo16.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msvideo'
cd `dirname msvideo/msrle32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/msvideo/msrle32'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. msrle32.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/msvideo/msrle32'
cd `dirname mswsock/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/mswsock'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. mswsock.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/mswsock'
cd `dirname netapi32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/netapi32'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/netapi32/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. access.c apibuf.c wksta.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/netapi32/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. access.c apibuf.c browsr.c nbcmdqueue.c nbnamecache.c nbt.c netapi32.c netbios.c wksta.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/netapi32'
cd `dirname ntdll/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/ntdll'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/ntdll/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. env.c error.c generated.c large_int.c path.c rtl.c rtlbitmap.c rtlstr.c string.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/ntdll/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cdrom.c critsection.c debugtools.c env.c error.c exception.c file.c heap.c large_int.c loader.c loadorder.c misc.c nt.c om.c path.c process.c reg.c relay.c resource.c rtl.c rtlbitmap.c rtlstr.c sec.c server.c signal_i386.c signal_powerpc.c signal_sparc.c string.c sync.c version.c thread.c time.c virtual.c wcstring.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/ntdll'
cd `dirname odbc32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/odbc32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. proxyodbc.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/odbc32'
cd `dirname ole32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/ole32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. antimoniker.c bindctx.c clipboard.c compobj.c compositemoniker.c datacache.c defaulthandler.c errorinfo.c filemoniker.c ftmarshal.c git.c hglobalstream.c ifs.c itemmoniker.c marshal.c memlockbytes.c moniker.c ole2.c ole2stubs.c ole2impl.c ole32_main.c oleobj.c oleproxy.c regsvr.c rpc.c stg_bigblockfile.c stg_stream.c storage32.c memlockbytes16.c ole16.c ole2_16.c ole2nls.c storage.c ole32res.rc version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/ole32'
cd `dirname oleacc/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/oleacc'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/oleacc'
cd `dirname oleaut32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/oleaut32'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/oleaut32/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. olefont.c safearray.c vartest.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/oleaut32/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. connpt.c dispatch.c hash.c oaidl_p.c oleaut.c olefont.c olepicture.c regsvr.c safearray.c stubs.c tmarshal.c typelib.c usrmarshal.c varformat.c variant.c ole2disp.c typelib16.c oleaut32.rc version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/oleaut32'
cd `dirname olecli/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/olecli'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. olecli_main.c olecli16.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/olecli'
cd `dirname oledlg/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/oledlg'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. insobjdlg.c oledlg_main.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/oledlg'
cd `dirname olepro32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/olepro32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. olepro32stubs.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/olepro32'
cd `dirname olesvr/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/olesvr'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. olesvr_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/olesvr'
cd `dirname psapi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/psapi'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. psapi_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/psapi'
cd `dirname qcap/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/qcap'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. qcap_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/qcap'
cd `dirname quartz/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/quartz'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. avisplit.c control.c enummedia.c enummoniker.c enumpins.c filesource.c filtergraph.c filtermapper.c main.c memallocator.c pin.c regsvr.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/quartz'
cd `dirname rasapi32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/rasapi32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. rasapi.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/rasapi32'
cd `dirname richedit/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/richedit'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. charlist.c reader.c text-writer.c richedit.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/richedit'
cd `dirname rpcrt4/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/rpcrt4'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/rpcrt4/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. rpc.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/rpcrt4/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cproxy.c cpsf.c cstub.c ndr_marshall.c ndr_midl.c ndr_ole.c ndr_stubless.c rpc_binding.c rpc_epmap.c rpc_message.c rpc_server.c rpcrt4_main.c rpcss_np_client.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/rpcrt4'
cd `dirname serialui/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/serialui'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. confdlg.c  serialui_rc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/serialui'
cd `dirname setupapi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/setupapi'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. devinst.c dirid.c install.c parser.c queue.c setupcab.c stubs.c devinst16.c infparse.c setupx_main.c virtcopy.c setupapi.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/setupapi'
cd `dirname shdocvw/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/shdocvw'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. classinfo.c events.c factory.c misc.c oleobject.c persist.c regsvr.c shdocvw_main.c webbrowser.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/shdocvw'
cd `dirname shell32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/shell32'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/shell32/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. generated.c shlfileop.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/shell32/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. authors.c brsfolder.c changenotify.c classes.c clipboard.c control.c dataobject.c debughlp.c dialogs.c dragdrophelper.c enumidlist.c folders.c iconcache.c memorystream.c pidl.c regsvr.c shell32_main.c shelllink.c shellole.c shellord.c shellpath.c shellreg.c shellstring.c shfldr_desktop.c shfldr_fs.c shfldr_mycomp.c shlexec.c shlfileop.c shlfolder.c shlfsbind.c shlmenu.c shlview.c shpolicy.c shv_bg_cmenu.c shv_item_cmenu.c systray.c shell.c shres.rc version.rc version16.rc   
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/shell32'
cd `dirname shfolder/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/shfolder'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. shfolder_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/shfolder'
cd `dirname shlwapi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/shlwapi'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/shlwapi/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. clist.c clsid.c generated.c path.c shreg.c string.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/shlwapi/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. assoc.c clist.c istream.c ordinal.c path.c reg.c regstream.c shlwapi_main.c string.c thread.c url.c wsprintf.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/shlwapi'
cd `dirname snmpapi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/snmpapi'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/snmpapi'
cd `dirname sti/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/sti'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. sti_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/sti'
cd `dirname tapi32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/tapi32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. assisted.c line.c phone.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/tapi32'
cd `dirname ttydrv/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/ttydrv'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. bitmap.c dc.c graphics.c objects.c palette.c ttydrv_main.c user.c wnd.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/ttydrv'
cd `dirname twain/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/twain'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. capability.c ds_audio.c ds_ctrl.c ds_image.c dsm_ctrl.c twain32_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/twain'
cd `dirname unicows/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/unicows'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/unicows'
cd `dirname url/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/url'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. url_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/url'
cd `dirname urlmon/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/urlmon'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/urlmon/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. generated.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/urlmon/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. umon.c urlmon_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/urlmon'
cd `dirname user/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/user'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/user/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. class.c generated.c input.c listbox.c msg.c sysparams.c win.c wsprintf.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/user/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. ../../controls/button.c ../../controls/combo.c ../../controls/desktop.c ../../controls/edit.c ../../controls/icontitle.c ../../controls/listbox.c ../../controls/menu.c ../../controls/scroll.c ../../controls/static.c ../../controls/uitools.c ../../windows/class.c ../../windows/clipboard.c ../../windows/cursoricon.c ../../windows/dce.c ../../windows/defdlg.c ../../windows/defwnd.c ../../windows/dialog.c ../../windows/driver.c ../../windows/input.c ../../windows/keyboard.c ../../windows/mdi.c ../../windows/message.c ../../windows/msgbox.c ../../windows/multimon.c ../../windows/nonclient.c ../../windows/painting.c ../../windows/queue.c ../../windows/rect.c ../../windows/scroll.c ../../windows/spy.c ../../windows/struct32.c ../../windows/syscolor.c ../../windows/sysmetrics.c ../../windows/sysparams.c ../../windows/timer.c ../../windows/user.c ../../windows/win.c ../../windows/winhelp.c ../../windows/winpos.c ../../windows/winproc.c cache.c caret.c dde/client.c dde/ddeml16.c dde/misc.c dde/server.c dialog16.c display.c exticon.c focus.c hook.c lstr.c message.c misc.c mouse.c msg16.c painting.c property.c resource.c text.c user_main.c wsprintf.c bidi16.c comm16.c hook16.c network.c user16.c wnd16.c resources/user32.rc resources/display.rc resources/mouse.rc resources/version16.rc   
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/user'
cd `dirname uxtheme/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/uxtheme'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. draw.c main.c metric.c msstyles.c property.c system.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/uxtheme'
cd `dirname version/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/version'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. info.c install.c resource.c ver16.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/version'
cd `dirname win32s/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/win32s'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. w32skernel.c w32sys.c win32s16.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/win32s'
cd `dirname winaspi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winaspi'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. aspi.c winaspi32.c winaspi16.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winaspi'
cd `dirname winedos/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winedos'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. devices.c dma.c dosaspi.c dosconf.c dosvm.c fpu.c himem.c int09.c int10.c int11.c int12.c int13.c int15.c int16.c int17.c int19.c int1a.c int20.c int21.c int25.c int26.c int29.c int2a.c int2f.c int31.c int33.c int41.c int4b.c int5c.c int67.c interrupts.c ioports.c module.c ppdev.c relay.c soundblaster.c timer.c vga.c vxd.c xms.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winedos'
cd `dirname wineps/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/wineps'
../../tools/makedep -I. -I. -I../../include -I../../include -I/usr/include/freetype2 -C. afm.c bitblt.c bitmap.c brush.c builtin.c clipping.c color.c download.c driver.c encode.c escape.c font.c glyphlist.c graphics.c init.c objects.c pen.c ppd.c ps.c text.c truetype.c type1.c type1afm.c type42.c data/agl.c data/AvantGarde_Book.c data/AvantGarde_BookOblique.c data/AvantGarde_Demi.c data/AvantGarde_DemiOblique.c data/Bookman_Demi.c data/Bookman_DemiItalic.c data/Bookman_Light.c data/Bookman_LightItalic.c data/Courier.c data/Courier_Bold.c data/Courier_BoldOblique.c data/Courier_Oblique.c data/Helvetica.c data/Helvetica_Bold.c data/Helvetica_BoldOblique.c data/Helvetica_Narrow.c data/Helvetica_Narrow_Bold.c data/Helvetica_Narrow_BoldOblique.c data/Helvetica_Narrow_Oblique.c data/Helvetica_Oblique.c data/NewCenturySchlbk_Bold.c data/NewCenturySchlbk_BoldItalic.c data/NewCenturySchlbk_Italic.c data/NewCenturySchlbk_Roman.c data/Palatino_Bold.c data/Palatino_BoldItalic.c data/Palatino_Italic.c data/Palatino_Roman.c data/Symbol.c data/Times_Bold.c data/Times_BoldItalic.c data/Times_Italic.c data/Times_Roman.c data/ZapfChancery_MediumItalic.c data/ZapfDingbats.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/wineps'
cd `dirname wininet/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/wininet'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/wininet/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. generated.c http.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/wininet/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cookie.c dialogs.c ftp.c gopher.c http.c internet.c netconnection.c urlcache.c utility.c wininet_main.c  rsrc.rc version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/wininet'
cd `dirname winmm/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/winmm/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. wave.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. driver.c joystick.c lolvldrv.c mci.c mmio.c playsound.c time.c winmm.c message16.c mmsystem.c sound16.c winmm_res.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm'
cd `dirname winmm/joystick/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/joystick'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. joystick.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/joystick'
cd `dirname winmm/mcianim/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/mcianim'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. mcianim.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/mcianim'
cd `dirname winmm/mciavi/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/mciavi'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. info.c mciavi.c mmoutput.c wnd.c  mciavi_res.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/mciavi'
cd `dirname winmm/mcicda/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/mcicda'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. mcicda.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/mcicda'
cd `dirname winmm/mciseq/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/mciseq'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. mcimidi.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/mciseq'
cd `dirname winmm/mciwave/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/mciwave'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. mciwave.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/mciwave'
cd `dirname winmm/midimap/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/midimap'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. midimap.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/midimap'
cd `dirname winmm/wavemap/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/wavemap'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. wavemap.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/wavemap'
cd `dirname winmm/winealsa/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/winealsa'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c audio_05.c alsa.c midi.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/winealsa'
cd `dirname winmm/winearts/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/winearts'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. arts.c audio.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/winearts'
cd `dirname winmm/wineaudioio/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/wineaudioio'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c audioio.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/wineaudioio'
cd `dirname winmm/winejack/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/winejack'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c jack.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/winejack'
cd `dirname winmm/winenas/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/winenas'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c nas.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/winenas'
cd `dirname winmm/wineoss/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winmm/wineoss'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. audio.c midi.c midipatch.c mixer.c mmaux.c oss.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winmm/wineoss'
cd `dirname winnls/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winnls'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winnls.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winnls'
cd `dirname winsock/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winsock'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/winsock/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. sock.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/winsock/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. async.c socket.c socket16.c version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winsock'
cd `dirname winspool/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/winspool'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/winspool/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. info.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/winspool/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. info.c wspool.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/winspool'
cd `dirname wintab32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/wintab32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. context.c manager.c wintab16.c     
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/wintab32'
cd `dirname wintrust/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/wintrust'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. wintrust_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/wintrust'
cd `dirname wow32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/wow32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. wow_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/wow32'
cd `dirname wsock32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/wsock32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. protocol.c service.c socket.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/wsock32'
cd `dirname d3d8/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/d3d8'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. basetexture.c cubetexture.c d3d8_main.c device.c directx.c drawprim.c indexbuffer.c resource.c shader.c stateblock.c surface.c swapchain.c texture.c utils.c vertexbuffer.c volume.c volumetexture.c vshaderdeclaration.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/d3d8'
cd `dirname d3d9/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/d3d9'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. basetexture.c cubetexture.c d3d9_main.c device.c directx.c indexbuffer.c pixelshader.c query.c resource.c stateblock.c surface.c swapchain.c texture.c vertexbuffer.c vertexdeclaration.c vertexshader.c volume.c volumetexture.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/d3d9'
cd `dirname d3dx8/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/d3dx8'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. d3dx8_main.c d3dxbuffer.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/d3dx8'
cd `dirname ddraw/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/ddraw'
cd `dirname tests/__depend__` && make depend
make[3]: Entering directory `/home/deaddevil66/wine/dlls/ddraw/tests'
../../../tools/makedep -I. -I. -I../../../include -I../../../include  -C. ddrawmodes.c      testlist.c
make[3]: Leaving directory `/home/deaddevil66/wine/dlls/ddraw/tests'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. d3dcommon.c d3ddevice/main.c d3ddevice/mesa.c d3dexecutebuffer.c d3dlight.c d3dmaterial.c d3dtexture.c d3dvertexbuffer.c d3dviewport.c direct3d/main.c direct3d/mesa.c mesa.c convert.c dclipper/main.c ddraw/hal.c ddraw/main.c ddraw/thunks.c ddraw/user.c dpalette/hal.c dpalette/main.c dsurface/dib.c dsurface/fakezbuffer.c dsurface/gamma.c dsurface/hal.c dsurface/main.c dsurface/thunks.c dsurface/user.c dsurface/wndproc.c helper.c main.c regsvr.c struct_convert.c  version.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/ddraw'
cd `dirname glu32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/glu32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. glu.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/glu32'
cd `dirname glut32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/glut32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. glut.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/glut32'
cd `dirname opengl32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/opengl32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. wgl.c opengl_norm.c opengl_ext.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/opengl32'
cd `dirname wined3d/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/wined3d'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. vertexshader.c wined3d_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/wined3d'
cd `dirname x11drv/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/dlls/x11drv'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. bitblt.c bitmap.c brush.c clipboard.c clipping.c codepage.c desktop.c dga2.c dib.c dib_convert.c dib_dst_swap.c dib_src_swap.c event.c graphics.c init.c keyboard.c mouse.c opengl.c palette.c pen.c scroll.c settings.c text.c window.c winpos.c x11ddraw.c x11drv_main.c xdnd.c xfont.c xrandr.c xrender.c xvidmode.c      
make[2]: Leaving directory `/home/deaddevil66/wine/dlls/x11drv'
../tools/makedep -I. -I. -I../include -I../include  -C.       
make[1]: Leaving directory `/home/deaddevil66/wine/dlls'
cd `dirname documentation/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/documentation'
../tools/makedep -I. -I. -I../include -I../include  -C.       
make[1]: Leaving directory `/home/deaddevil66/wine/documentation'
cd `dirname include/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/include'
../tools/makedep -I. -I. -I../include -I../include  -C.      amvideo.idl comcat.idl docobj.idl exdisp.idl oaidl.idl objidl.idl ocidl.idl oleidl.idl servprov.idl shobjidl.idl shtypes.idl strmif.idl unknwn.idl urlmon.idl wtypes.idl 
make[1]: Leaving directory `/home/deaddevil66/wine/include'
cd `dirname libs/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/libs'
cd `dirname port/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/libs/port'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. getopt.c getopt1.c getpagesize.c gettid.c interlocked.c lstat.c memcpy_unaligned.c memmove.c mkstemps.c pread.c pwrite.c sigsetjmp.c spawn.c statfs.c strcasecmp.c strerror.c strncasecmp.c usleep.c      
make[2]: Leaving directory `/home/deaddevil66/wine/libs/port'
cd `dirname unicode/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/libs/unicode'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. casemap.c collation.c compose.c cptable.c fold.c mbtowc.c sortkey.c string.c utf8.c wctomb.c wctype.c c_037.c c_042.c c_424.c c_437.c c_500.c c_737.c c_775.c c_850.c c_852.c c_855.c c_856.c c_857.c c_860.c c_861.c c_862.c c_863.c c_864.c c_865.c c_866.c c_869.c c_874.c c_875.c c_878.c c_932.c c_936.c c_949.c c_950.c c_1006.c c_1026.c c_1250.c c_1251.c c_1252.c c_1253.c c_1254.c c_1255.c c_1256.c c_1257.c c_1258.c c_10000.c c_10006.c c_10007.c c_10029.c c_10079.c c_10081.c c_20866.c c_20932.c c_28591.c c_28592.c c_28593.c c_28594.c c_28595.c c_28596.c c_28597.c c_28598.c c_28599.c c_28600.c c_28603.c c_28604.c c_28605.c c_28606.c      
make[2]: Leaving directory `/home/deaddevil66/wine/libs/unicode'
cd `dirname uuid/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/libs/uuid'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dx8guid.c dx9guid.c dxguid.c uuid.c      
make[2]: Leaving directory `/home/deaddevil66/wine/libs/uuid'
cd `dirname wine/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/libs/wine'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. config.c debug.c ldt.c loader.c port.c      
make[2]: Leaving directory `/home/deaddevil66/wine/libs/wine'
cd `dirname wpp/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/libs/wpp'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. preproc.c wpp.c      ppy.y ppl.l
make[2]: Leaving directory `/home/deaddevil66/wine/libs/wpp'
../tools/makedep -I. -I. -I../include -I../include  -C.       
make[1]: Leaving directory `/home/deaddevil66/wine/libs'
cd `dirname loader/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/loader'
../tools/makedep -I. -I. -I../include -I../include  -C. glibc.c kthread.c main.c pthread.c      
make[1]: Leaving directory `/home/deaddevil66/wine/loader'
cd `dirname programs/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/programs'
cd `dirname avitools/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/avitools'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. aviinfo.c aviplay.c icinfo.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/avitools'
cd `dirname clock/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/clock'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. license.c main.c winclock.c License_En.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/clock'
cd `dirname cmdlgtst/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/cmdlgtst'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. cmdlgtst.c  cmdlgr.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/cmdlgtst'
cd `dirname control/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/control'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. control.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/control'
cd `dirname expand/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/expand'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. expand.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/expand'
cd `dirname notepad/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/notepad'
../../tools/makedep -I. -I. -I../../include -I../../include -I../../include/msvcrt -C. License_En.c dialog.c license.c main.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/notepad'
cd `dirname progman/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/progman'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dialog.c group.c grpfile.c license.c main.c program.c string.c License_En.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/progman'
cd `dirname regedit/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/regedit'
../../tools/makedep -I. -I. -I../../include -I../../include -I../../include/msvcrt -C. about.c childwnd.c edit.c framewnd.c listview.c main.c regedit.c regproc.c treeview.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/regedit'
cd `dirname regsvr32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/regsvr32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. regsvr32.c  regsvr32.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/regsvr32'
cd `dirname rpcss/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/rpcss'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. epmap_server.c np_server.c rpcss_main.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/rpcss'
cd `dirname rundll32/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/rundll32'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. rundll32.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/rundll32'
cd `dirname start/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/start'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. start.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/start'
cd `dirname uninstaller/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/uninstaller'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/uninstaller'
cd `dirname view/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/view'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. init.c view.c winmain.c  viewrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/view'
cd `dirname wcmd/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/wcmd'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. batch.c builtins.c directory.c wcmdmain.c  wcmdrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/wcmd'
cd `dirname wineboot/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/wineboot'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. wineboot.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/wineboot'
cd `dirname winecfg/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winecfg'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. appdefaults.c drive.c main.c properties.c winecfg.c x11drvdlg.c  winecfg.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winecfg'
cd `dirname wineconsole/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/wineconsole'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. curses.c dialog.c registry.c user.c wineconsole.c  wineconsole_res.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/wineconsole'
cd `dirname winedbg/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winedbg'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. break.c db_disasm.c display.c expr.c ext_debugger.c gdbproxy.c hash.c info.c memory.c module.c msc.c registers.c source.c stabs.c stack.c types.c winedbg.c      dbg.y debug.l
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winedbg'
cd `dirname winefile/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winefile'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. license.c splitpath.c winefile.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winefile'
cd `dirname winemenubuilder/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winemenubuilder'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winemenubuilder.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winemenubuilder'
cd `dirname winemine/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winemine'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dialog.c main.c  rsrc.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winemine'
cd `dirname winepath/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winepath'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winepath.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winepath'
cd `dirname winetest/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winetest'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. main.c send.c util.c  winetest.rc    
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winetest'
cd `dirname winevdm/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winevdm'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winevdm.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winevdm'
cd `dirname winhelp/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winhelp'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winhelp.c hlpfile.c macro.c string.c  rsrc.rc    macro.lex.l
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winhelp'
cd `dirname winver/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/programs/winver'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. winver.c      
make[2]: Leaving directory `/home/deaddevil66/wine/programs/winver'
../tools/makedep -I. -I. -I../include -I../include  -C.       
make[1]: Leaving directory `/home/deaddevil66/wine/programs'
cd `dirname server/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/server'
../tools/makedep -I. -I. -I../include -I../include  -C. async.c atom.c change.c clipboard.c console.c context_i386.c context_powerpc.c context_sparc.c debugger.c device.c event.c fd.c file.c handle.c hook.c main.c mapping.c mutex.c named_pipe.c object.c process.c ptrace.c queue.c registry.c request.c semaphore.c serial.c signal.c smb.c snapshot.c sock.c thread.c timer.c token.c trace.c unicode.c user.c window.c      
make[1]: Leaving directory `/home/deaddevil66/wine/server'
cd `dirname tools/__depend__` && make depend
make[1]: Entering directory `/home/deaddevil66/wine/tools'
cd `dirname widl/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/tools/widl'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. header.c proxy.c utils.c widl.c      parser.y parser.l
make[2]: Leaving directory `/home/deaddevil66/wine/tools/widl'
cd `dirname winebuild/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/tools/winebuild'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. import.c main.c parser.c relay.c res16.c res32.c spec16.c spec32.c utils.c      
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winebuild'
cd `dirname winedump/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/tools/winedump'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. debug.c main.c misc.c msmangle.c ne.c output.c pe.c search.c symbol.c      
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winedump'
cd `dirname winegcc/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/tools/winegcc'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. utils.c winegcc.c winewrap.c      
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winegcc'
cd `dirname wmc/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/tools/wmc'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. lang.c mcl.c utils.c wmc.c write.c      mcy.y
make[2]: Leaving directory `/home/deaddevil66/wine/tools/wmc'
cd `dirname wrc/__depend__` && make depend
make[2]: Entering directory `/home/deaddevil66/wine/tools/wrc'
../../tools/makedep -I. -I. -I../../include -I../../include  -C. dumpres.c genres.c newstruc.c readres.c utils.c wrc.c writeres.c      parser.y parser.l
make[2]: Leaving directory `/home/deaddevil66/wine/tools/wrc'
../tools/makedep -I. -I. -I../include -I../include  -C. bin2res.c fnt2bdf.c makedep.c      
make[1]: Leaving directory `/home/deaddevil66/wine/tools'
./tools/makedep -I. -I. -I./include -I./include  -C.       
make[1]: Entering directory `/home/deaddevil66/wine/libs'
make[2]: Entering directory `/home/deaddevil66/wine/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/port'
make[2]: Entering directory `/home/deaddevil66/wine/libs/unicode'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/unicode'
make[2]: Entering directory `/home/deaddevil66/wine/libs/uuid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/uuid'
make[2]: Entering directory `/home/deaddevil66/wine/libs/wine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/wine'
make[2]: Entering directory `/home/deaddevil66/wine/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/libs/wpp'
make[1]: Leaving directory `/home/deaddevil66/wine/libs'
make[1]: Entering directory `/home/deaddevil66/wine/tools'
make[2]: Entering directory `/home/deaddevil66/wine/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/widl'
make[2]: Entering directory `/home/deaddevil66/wine/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winebuild'
make[2]: Entering directory `/home/deaddevil66/wine/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winedump'
make[2]: Entering directory `/home/deaddevil66/wine/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/winegcc'
make[2]: Entering directory `/home/deaddevil66/wine/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/deaddevil66/wine/tools/wmc'
make[2]: Entering directory `/home/deaddevil66/wine/tools/wrc'
gcc -c -I. -I. -I../../include -I../../include  -DINCLUDEDIR="\"/usr/local/include/wine\""  -Wall -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o newstruc.o newstruc.c
make[2]: Leaving directory `/home/deaddevil66/wine/tools/wrc'
make[1]: Leaving directory `/home/deaddevil66/wine/tools'
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:764: error: lvalue required as increment operand
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:875: error: lvalue required as increment operand
make[2]: *** [newstruc.o] Error 1
make[1]: *** [wrc] Error 2
make: *** [tools] Error 2

```

help!!!! :confused:

---

