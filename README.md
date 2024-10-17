# openwrt-ipq50xx

>
> NOTE¹: For 160MHz, `Country Code`, `Width` and `Channel` need to be set correctly. And wait 1 minute for radar detection, then the WiFi will be appeareed.
>
>	```
>	uci -q batch <<-EOF
>		wireless.radio1.country='CN'
>		wireless.radio1.htmode='HE160'
>		wireless.radio1.channel='64'
>	EOF
>	```

## How to build

OS: `Ubuntu 20.04 (focal)`

```bash
# Install dependencies
sudo add-apt-repository ppa:npalix/coccinelle
sudo apt update
sudo apt install build-essential clang flex g++ gawk gcc-multilib gettext \
  git libncurses5-dev libssl-dev python3-distutils rsync unzip zlib1g-dev \
  coccinelle

# Clone this repo
git clone https://github.com/zclkkk/openwrt-ipq50xx
cd openwrt-ipq50xx

# Update and install feeds
./scripts/feeds update -a
./scripts/feeds install -a

# Configure
make menuconfig

# Download
make -j16 download

# Build
make -j$(nproc)
```

## Related links

[`openwrt/openwrt`](https://github.com/openwrt/openwrt) - Openwrt official repository

[`qsdk`](https://git.codelinaro.org/clo/qsdk) - QSDK official repository

[`quic/qca-sdk-nss-fw`](https://github.com/quic/qca-sdk-nss-fw) - NSS firmware

[`quic/upstream-wifi-fw`](https://github.com/quic/upstream-wifi-fw) - WiFi firmware

[`qca/qca-swiss-army-knife`](https://github.com/qca/qca-swiss-army-knife) - BDF tools

[`Telecominfraproject/wlan-ap`](https://github.com/Telecominfraproject/wlan-ap) - another Openwrt which support `ipq50xx`
