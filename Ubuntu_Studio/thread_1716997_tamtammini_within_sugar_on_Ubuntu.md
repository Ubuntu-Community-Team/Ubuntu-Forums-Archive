---
title: "tamtammini within sugar on Ubuntu"
date: 2011-03-29
forum: Ubuntu Studio
---

### Post by andmod on 2011-03-29
I am trying to run tamtammini-57.xo within the sugar environment on Ubuntu 10.10. While several activities run perfectly (i.e. speak.activity) Tamtammini gives no sound. Down below is my logfile. Does anybody have an idea what the problem could be? 
Thank you, Andrea

** Message: pygobject_register_sinkfunc is deprecated (HippoCanvasBox)
1301392836.158145 DEBUG root: Debug Level 0
1301392836.158415 DEBUG root: INFO: loaded TAMTAM_ROOT=/home/jux/Activities/TamTamMini.activity
1301392836.214454 DEBUG root: skip /home/jux/Activities/TamTamMini.activity/common/Util/Clooper/linux64_511_deb blobs: /home/jux/Activities/Tam
TamMini.activity/common/Util/Clooper/linux64_511_deb/aclient.so: falsche ELF-Klasse: ELFCLASS64
1301392836.216862 DEBUG root: skip /home/jux/Activities/TamTamMini.activity/common/Util/Clooper/linux64_510 blobs: /home/jux/Activities/TamTamM
ini.activity/common/Util/Clooper/linux64_510/aclient.so: falsche ELF-Klasse: ELFCLASS64
1301392836.218069 DEBUG root: skip /home/jux/Activities/TamTamMini.activity/common/Util/Clooper/linux32_508 blobs: libcsound.so.5.1: Kann die S
hared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
1301392836.226332 DEBUG root: use /home/jux/Activities/TamTamMini.activity/common/Util/Clooper/linux32_511_deb blobs
1301392836.293436 DEBUG root: datastore.get
1301392836.298367 WARNING root: .has_key() is deprecated, use 'in'
1301392836.303999 DEBUG root: *** Act fe6faa0ce02bb0dce54e1510cf9c965b80cde2b4, mesh instance None, scope private
1301392836.326327 DEBUG root: PaletteWindow.popdown immediate True
1301392836.335281 DEBUG root: PaletteWindow.popdown immediate True
1301392836.340254 WARNING root: No gtk.AccelGroup in the top level window.
1301392836.344155 WARNING root: No gtk.AccelGroup in the top level window.
/usr/lib/python2.6/dist-packages/sugar/graphics/window.py:290: DeprecationWarning: use toolbar_box instead of toolbox
  warnings.warn('use toolbar_box instead of toolbox', DeprecationWarning)
Logging disabled on purpose
PortMIDI real time MIDI plugin for Csound
virtual_keyboard real time MIDI plugin for Csound
PortAudio real-time audio module for Csound
0dBFS level = 32768.0
Csound version 5.12 (double samples) Sep 15 2010
libsndfile-1.0.21
UnifiedCSD:  /home/jux/Activities/TamTamMini.activity/common/Resources/tamtamorc.csd
STARTING FILE
Creating options
Herstellen des Orchesters
Creating score
orchname:  /tmp/csound-uN7ijG.orc
scorename: /tmp/csound-QRX3dJ.sco
rtaudio: PortAudio module enabled ... using blocking interface
RAWWAVE_PATH: /usr/share/stk/rawwaves/
rtmidi: PortMIDI module enabled
orch compiler:
        opcode  homeSine        a       kki     
        opcode  synthGrain      a       aaiiii  
        opcode  ControlMatrice  i       iikkkk  
        opcode  SourceMatrice   i       iaaaa   
        opcode  FxMatrice       i       iaaaa   
        opcode  controller      k       ii      
        opcode  source  a       ii      
        opcode  effects a       ii      
        instr   200     
        instr   5600
        instr   5400    
        instr   5401    
        instr   5201    
        instr   5202    
        instr   5212    
        instr   6000    
        instr   5204    
        instr   5203    
        instr   5000    
        instr   5022    
        instr   5023    
        instr   5001    5002    5003    5004    5005    5006    5007    5008    5009    5010    
        instr   5101    5102    5103    5104    5105    5106    5107    5108    5109    5110    
        instr   5011    5012    5013    5014    5015    5016    5017    5018    5019    5020    
        instr   5111    5112    5113    5114    5115    5116    5117    5118    5119    5120    
        instr   5021    
sorting score ...
        ... getan
Csound version 5.12 (double samples) Sep 15 2010
displays suppressed
0dBFS level = 32768.0
orch now loaded
audio buffered in 256 sample-frame blocks
SECTION 1:
/home/jux/Activities/TamTamMini.activity/Mini/miniTamTamMain.py:92: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/home/jux/Activities/TamTamMini.activity/Mini/miniTamTamMain.py:187: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(self.geneSlider,Tooltips.COMPL)
/home/jux/Activities/TamTamMini.activity/Mini/miniTamTamMain.py:200: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(self.beatSlider,Tooltips.BEAT)
/home/jux/Activities/TamTamMini.activity/Mini/miniTamTamMain.py:217: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(tempoSlider,Tooltips.TEMPO)
/home/jux/Activities/TamTamMini.activity/Mini/miniTamTamMain.py:230: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(volumeSlider,Tooltips.VOL)
/home/jux/Activities/TamTamMini.activity/Mini/miniTamTamMain.py:258: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(generateBtn,Tooltips.GEN)
/home/jux/Activities/TamTamMini.activity/Mini/miniTamTamMain.py:294: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(drum, hint)
/usr/lib/python2.6/dist-packages/sugar/graphics/window.py:294: DeprecationWarning: use toolbar_box instead of toolbox
  warnings.warn('use toolbar_box instead of toolbox', DeprecationWarning)
/home/jux/Activities/TamTamMini.activity/Mini/miniToolbars.py:27: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/home/jux/Activities/TamTamMini.activity/Mini/InstrumentPanel.py:63: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/home/jux/Activities/TamTamMini.activity/Mini/InstrumentPanel.py:182: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(self.loadData["btn"],str(category))
/home/jux/Activities/TamTamMini.activity/Mini/InstrumentPanel.py:226: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(self.loadData["instBox"],str(self.instrumentDB.instNamed[instrument].nameTooltip))
1301392837.395579 DEBUG root: Activity.__canvas_map_cb
1301392837.401996 DEBUG root: ActivityService.set_active: 1.
** (sugar-activity:3526): DEBUG: Got client ID "101728db4a96b880e130139283758456500000034680000"
** (sugar-activity:3526): DEBUG: Setting initial properties
** (sugar-activity:3526): DEBUG: Received SaveYourself(SmSaveLocal, !Shutdown, SmInteractStyleNone, !Fast) in state idle
** (sugar-activity:3526): DEBUG: Sending SaveYourselfDone(True) for initial SaveYourself
** (sugar-activity:3526): DEBUG: Received SaveComplete message in state save-yourself-done
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
insert_score_event(): invalid instrument number or name
1301392868.150118 DEBUG root: Palette.popup immediate False
1301392868.508538 DEBUG root: PaletteWindow.popdown immediate True
1301392868.509040 DEBUG root: Activity.save: '631250e8-9959-42a9-8e64-c26acde4db20'
1301392868.751866 DEBUG root: datastore.write
1301392868.752111 DEBUG root: dbus_helpers.update: 631250e8-9959-42a9-8e64-c26acde4db20, /home/jux/.sugar/default/org.laptop.TamTamMini/instance/1301392868, {dbus.String(u'activity_id'): dbus.ByteArray('fe6faa0ce02bb0dce54e1510cf9c965b80cde2b4', variant_level=1), dbus.String(u'title_set_by_user'): dbus.ByteArray('1', variant_level=1), dbus.String(u'uid'): dbus.ByteArray('631250e8-9959-42a9-8e64-c26acde4db20', variant_level=1), dbus.String(u'tags'): dbus.String(u'', variant_level=1), dbus.String(u'timestamp'): 1301392868, dbus.String(u'activity'): dbus.ByteArray('org.laptop.TamTamMini', variant_level=1), dbus.String(u'mtime'): '2011-03-29T12:01:08.752050', dbus.String(u'description'): dbus.String(u'', variant_level=1), dbus.String(u'title'): dbus.ByteArray('TamTamMini Aktivit\xc3\xa4t', variant_level=1), dbus.String(u'checksum'): dbus.ByteArray('d41d8cd98f00b204e9800998ecf8427e', variant_level=1), 'tamtam_subactivity': 'mini', dbus.String(u'keep'): dbus.ByteArray('0', variant_level=1), dbus.String(u'icon-color'): dbus.ByteArray('#00A0FF,#FF8F00', variant_level=1), dbus.String(u'share-scope'): dbus.ByteArray('private', variant_level=1), dbus.String(u'preview'): '<omitted>', dbus.String(u'mime_type'): dbus.String(u'', variant_level=1)}, True
1301392868.757511 DEBUG root: Written object 631250e8-9959-42a9-8e64-c26acde4db20 to the datastore.
1301392868.793594 DEBUG root: Activity.__save_cb
inactive allocs returned to freespace
end of score.              overall amps:      0.0      0.0
           overall samples out of range:        0        0
0 errors in performance
1301392870.900543 WARNING root: No gtk.AccelGroup in the top level window.
1301392870.901070 WARNING root: No gtk.AccelGroup in the top level window.
1301392870.903590 DEBUG root: PaletteWindow.popdown immediate True
1301392870.905475 DEBUG root: PaletteWindow.popdown immediate True
1301392870.909972 DEBUG root: PaletteWindow.popdown immediate True
1301392870.926053 DEBUG root: Quitting the activity process.
1301392870.943408 DEBUG root: _cleanup_temp_files
Exited with status 0, pid 3526 data (None, <open file '<fdopen>', mode 'w' at 0x9c0a700>, dbus.ByteArray('fe6faa0ce02bb0dce54e1510cf9c965b80cde2b4', variant_level=1))

---

### Post by freakalad on 2012-01-30
I've installed a fresh OS, based on Ubuntu, via Trisquel 5.

Unfortunately this problem persists, with no solution in sight.

Seems a problem related to CSound, and I just don't know how to resolve the issue

---

