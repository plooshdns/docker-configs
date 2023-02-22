# ⚠️⚠️ TESTING NOT COMPLETED ⚠️⚠️
Some edge cases can fail

# PlooshDNS configs

Internally we run bare-metal, but for some people docker is just easier to manage. 
## This will expose many ports, you have been warned
Docker setup (recommended to all):
1. Install docker, docker compose etc
2. Run `docker compose up --build -d`


Manual setup (recommended for performance critical applications, only a few ms but scales):
1. Install PiHole eg: `curl -sSL https://install.pi-hole.net | sudo bash`
2. Install AdGuard Home eg: `curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sudo sh -s -- -v`
3. Install unbound (use your package manager)
4. Copy network configuration files (you just need the ip of the machine to have another loopback device other then 127.0.0.1 to identify it better)

a. Copy the **contents** of the `systemd-networkd` to `/etc/systemd/network`

b. **Edit the contents of the file at `/etc/netplan/01-netcfg.yml` to include the added bits with vETH**

5. Copy the rest of the config files (since this was taylored for the docker container, you'll need to modify the config either before or after initial deployment)
6. Restart neccesary services or reboot
7. Log onto PiHole and AdGuard and fix any broken parts.
