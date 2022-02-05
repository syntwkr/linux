PEARTUUID
[ira@arch-box ~]$ ls -l /dev/disk/by-partuuid/
total 0
lrwxrwxrwx 1 root root 15 Jan 14 10:25 d1292e32-7a74-4f6c-9ec6-d97335ec8865 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Jan 14 10:25 ec5021fe-8b90-489e-a005-d9ca9bd84bc7 -> ../../nvme0n1p2

https://wiki.archlinux.org/title/EFISTUB#efibootmgr



EFIBOOTMGR
[ira@arch-box ~]$ efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0002,0003,0005,0000,0001
Boot0000* Windows Boot Manager  HD(1,GPT,f164c945-0dc3-4af7-8b27-baeca9795ec5,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...T................
Boot0001* Internal Storage  FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)SDD.
Boot0002* USB Storage  FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)USB.
Boot0003* PXE Network  FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)PXE.
Boot0005* Arch Linux  HD(1,GPT,d1292e32-7a74-4f6c-9ec6-d97335ec8865,0x800,0x200000)/File(\vmlinuz-linux)r.o.o.t.=.P.A.R.T.U.U.I.D.=.e.c.5.0.2.1.f.e.-.8.b.9.0.-.4.8.9.e.-.a.0.0.5.-.d.9.c.a.9.b.d.8.4.b.c.7. .r.w. .i.n.i.t.r.d.=.\.i.n.i.t.r.a.m.f.s.-.l.i.n.u.x...i.m.g.

ADDING CUSTOM KERNEL TO EFIBOOTMGR
efibootmgr --disk /dev/nvme0n1p1 --part 1 --create --label "Surface Arch Linux" --loader /vmlinuz-linux-surface --unicode 'root=PARTUUID=ec5021fe-8b90-489e-a005-d9ca9bd84bc7 rw initrd=\initramfs-linux-surface.img' --verbose
