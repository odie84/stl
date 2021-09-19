# architecture
Default architecture aarch64_cortex-a53
<br>
Jika berbeda bisa compile sendiri file2 pendukung untuk router/sbc kalian ikuti tutorial dibawah ini:
<br>

1)apt update -y && apt upgrade && apt-get -y install tar build-essential asciidoc binutils bzip2 gawk rsync gettext git libncurses5-dev libz-dev patch unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler
<br>

2)openwrt-sdk
<br>
Contoh download openwrt-sdk untuk architecture aarch64_cortex-a53
<br>
openwrt-sdk yang lain bisa download dilink https://downloads.openwrt.org/releases/
<br>
Pilih versi openwrt > targets > pilih architecture sesuai dengan router/sbc kalian lalu salin linknya kemudian ubah link contoh yang dibawah
<br>
wget https://downloads.openwrt.org/releases/21.02.0-rc3/targets/sunxi/cortexa53/openwrt-sdk-21.02.0-rc3-sunxi-cortexa53_gcc-8.4.0_musl.Linux-x86_64.tar.xz
<br>
tar -xf openwrt-sdk-21.02.0-rc3-sunxi-cortexa53_gcc-8.4.0_musl.Linux-x86_64.tar.xz
<br>
cd openwrt-sdk-21.02.0-rc3-sunxi-cortexa53_gcc-8.4.0_musl.Linux-x86_64

3)badvpn-tun2socks
<br>
git clone https://github.com/yazdan/tun2socks-Openwrt
<br>
cp -rf tun2socks-Openwrt/badvpn package/
<br>
rm -rf tun2socks-Openwrt/
<br>
make defconfig
<br>
make menuconfig
<br>
Pilih Network > VPN > badvpn > exit > save
<br>
make package/badvpn/compile V=99
<br><br>

4)corkscrew
<br>
git clone https://github.com/pfalcon/openwrt-packages.git
<br>
cp -rf openwrt-packages/net/corkscrew package/
<br>
rm -rf openwrt-packages
<br>
make menuconfig
<br>
Pilih Network > SSH > corkscrew > exit > save
<br>
make package/corkscrew/compile V=99
<br><br>

5)sshpass
<br>
mkdir -p package/sshpass
<br>
wget --no-check-certificate "https://www.dropbox.com/s/kr1hfprl5uwrm6u/sshpass-1.06.zip" && unzip sshpass-1.06.zip && rm -rf sshpass-1.06.zip
<br>
mv sshpass-1.06 package/sshpass/src
<br>
chmod +x package/sshpass/src/*
<br>
wget --no-check-certificate "https://www.dropbox.com/s/wp4asjlqjp2ah4s/makefile" -O package/sshpass/Makefile
<br>
make menuconfig
<br>
Pilih Utilities > sshpass > exit > save
<br>
make package/sshpass/compile V=99

# stl
wget --no-check-certificate "https://raw.githubusercontent.com/wegare123/stl/main/stl/install.sh" -O ~/install.sh && chmod 777 ~/install.sh && ~/./install.sh

# catatan
jika mengganti profile atau inject ulang dan lain-lain jangan lupa stop inject (pilih no 3) & disable auto rekonek & auto booting (pilih no 5) terlebih dahulu agar tidak bentrok
