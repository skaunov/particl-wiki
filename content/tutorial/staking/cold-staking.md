---
title: Cold staking setup
subtitle: How to secure Particl network while keeping your coins offline, away from malicious hackers 
slug: 
weight: 2
tags:
  - staking
  - pools
  - DSD
  - important
---

Before we dive into this guide, you might want to familiarize yourself with [theory of cold staking](/learn/staking/intro#cold-staking), so that you know what we're doing and why.

Particl's cold staking setup is quite flexible, meaning there are many options how to stake – each approach has its pros and cons. This guide will outline all the possible variants, so that you can choose your own balance between convenience, privacy and security.


## Where will you stake?

{{< hint info >}}
We won't mention "classic" [standalone staking](/tutorial/staking/intro/), which happens automatically in your unlocked wallet and therefore isn't a case of cold staking.
{{< /hint >}}

First, you need to decide where (or how) will you stake.

With Particl cold staking, you have the following options:

- **Staking on your own "DSD"** – Dedicated Staking Devices (or "DSD" for short) are usually small single-board computers (like Raspberry Pi 3+ or Rock64) or even servers/VPS, that are running 24/7 and therefore are ideal for staking non-stop. These are ideal for larger hodlers, geeks and tinkerers, anybody who wants total control over their funds and support the network with full node.
- **Staking on staking pool** – Staking pools are in a way DSDs as well, but offered for public. As with mining pools, all pool members are staking together and all staking rewards are proportionally split between its members. That's why pools are ideal for smaller holders, but also beginners and those who are not comfortable playing with command line – kind of a "connect, stake & forget" approach.

**Based on your preferences, pick one**. If you're not sure, don't worry and start with staking on a pool. You can switch to DSD anytime you want (or the other way around).

|                            | Staking on DSD             | Staking on pool                   |
|----------------------------|----------------------------|-----------------------------------|
| **Setup difficulty**       | higher                     | trivial                           |
| **Setup cost**             | hardware & energy          | _none_                            |
| **Security**               | your hardware, your rules  | you're depending on pool operator |
| **Staking rewards**        | 100% yours                 | pool incl. fees (usually 1–3 %)   |
| **Ideal for hodlers with** | approx. 4,000+ PART        | any amount (even small)           |
| **Network effect**         | full node – increases decentralization | centralizes funds on few bigger nodes |
| **Setup guide**            | [Staking on DSD with Partyman](/tutorial/staking/on-dedicated-device/) | – |


## Get staking public key

Now it's time to get your public key for staking. You will need it for configuring your main wallet to delegate the staking to the staking device (Pool/DSD). Based on your choice, follow the links below to get your public key:

{{< tabs "get-pubkey" >}}

{{< tab "Staking Pool" >}}
### Using Staking Pool

Getting the public key from a staking Pool couldn't be easier. Visit our [list of available Staking Pools](/learn/staking/pools/#available-staking-pools), pick one that you like and visit it's homepage. Right at the top, you'll see the **public key for staking** (or "**Pool address**" on some pools).

{{< label info >}}Note{{< /label >}} Pool public keys begin with `pcs` and usually look similar to this:
```
pcs14ch7w7ue2q8kadljsl42wehfw8tm99yxsez4kz
```
{{< /tab >}}

{{< tab "Dedicated Staking Device" >}}
### Using Dedicated Staking Device

If you haven't set up your DSD yet, follow [Staking on DSD with Partyman](/tutorial/staking/on-dedicated-device/) guide to install latest Particl Core daemon on your device, generate a new wallet and a new staking public key along with it.

{{< label info >}}Note{{< /label >}} Public keys generated by Partyman begin with `PPART` and usually look similar to this:
```
PPARTKVAobLsHTQpZ5LzFHcZw8LD4sEEVu23mcuAqCjDaaNJgypRmUUpFKMxbmn1hZ5V2J9SaG1QusCrngC9iiBAA8LvxVRx9aLBPjGeY4PtrxzW
```
{{< /tab >}}

{{< /tabs >}}

When you get the public key for staking, **copy it and save it for later**.


## Connect your wallet

The staking device part is now successfully configured – now onto connecting our wallet to it.

Particl has a nice selection of various wallets for different needs. Comparing all their features is out of the scope of this guide, but feel free to check [Particl wallets: overview](/learn/wallets/overview) for more information. We'll focus here on the staking aspects only.

- **[Particl Desktop](/tutorial/wallets/particl-desktop/)** – our flagship wallet, with easy cold staking configuration
- **[Particl Core](/tutorial/wallets/particl-core/)** – time-tested wallet with advanced features ([Coin Control](/tutorial/privacy/coin-control/)) and compatibility with [hardware wallets](/learn/wallets/hardware)
- **[Particl Copay](/tutorial/wallets/particl-copay/)** – mainly for mobile, multiplatform wallet with user-friendly [multi-sig](/tutorial/security/multisig/) feature
- **[Hardware wallets](/learn/wallets/hardware)** (Trezor & Ledger wallets) – secure hardware devices for storing cryptocurrency private keys, offline and away from hackers

{{< tabs "connect-wallet" >}}

{{< tab "Particl Desktop" >}}
### Particl Desktop

1. Open Particl Desktop
2. On **Overview** page, locate the Cold Staking widget (in right sidebar) and click on the `+` button in it
3. Paste the **staking public key**/**pool address** (that you saved before)
4. Click `Enable cold staking` button to confirm
{{< /tab >}}

{{< tab "Particl Core / Ledger" >}}
### Particl Core

1. Open Particl Core
2. Go to **Window → Staking Setup**
3. Paste the **staking public key**/**pool address** (that you saved before) into the **Cold staking change address** field and click `Apply`
{{< /tab >}}

{{< tab "Particl Electrum" >}}
### Particl Electrum

1. Open Particl Electrum
2. Enter the cold staking change address (a pool's public address, for example) you want to stake to in the Tools/Preferences/ColdStaking menu
3. Enable Coin Control by opening the View tab and clicking on Show Coins
4. Open the Coins page by clicking on the Coins tab that should now show up on your client
5. Select all the outputs you want to cold stake, right-click on them, and then click on Spend
6. Open the Receive page and create a new regular address
7. Copy the address that was just created in your clipboard; we'll use it to enable cold staking
8. In the Send page, paste the address you've just copied and put a dust figure like (e.g., 0.1) in the Amount text field
9. Before sending the transaction, make sure that Electrum tells you that "coin control is active" with the correct number of outputs at the bottom of your screen
10. Click on "Pay..." to initiate the payment. A confirmation window should now appear. Ensure that the information is correct, and then click on Send
11. You can confirm that cold staking has been successfully activated by going in the Coins page once again. You should see a new output represented by a 256bit address that should be equal to the sum of the value of the outputs you've selected for staking, minus the change and network fees
12. You can further confirm that the staking pool has detected it by copying this new 256-bit address in your keyboard and going to the following link: `https://IP_ADDRESS_OR_URL_OF_THE_POOL/api/json/address/YOUR_256_BIT_ADDRESS_HERE`. Here's an example of how it may look with the proper information added: `https://coldstakingpool.com/api/json/address/2voNrBmH275emiEX95na1eFBJemWg9fkDPJLIJxxWdR9c6Qi7x6`. If your outputs have been detected by the pool, your browser should display the correct number of satoshis currently cold staking in the pool
13. Once that output matures (255 blocks), any stakes made by the pool will accumulate in that address in proportion to your balance relative to the total amount of coins staking in the pool
14. Note that if you move that output (256-bit address), the spending address will change and will start accumulating from zero again
15. If you want to increase your privacy while staking, you can indicate to Particl Electrum a list of change addresses in the Tools/Preferences/ColdStaking menu. Now, any change will automatically go to a randomly selected spend address from your list
{{< /tab >}}

{{< tab "Particl Copay" >}}
### Particl Copay

1. Open Particl Copay
2. Select your wallet from overview
3. Click on **Staking** tab/icon in the bottom navigation
4. You should see a "Wallet not staking yet" screen – click on the `Setup Cold Staking` button
5. Paste the **staking public key**/**pool address** (that you saved before) into the **Staking key (Pool address or Node public key)** field; you can optionally also label the key so you know _where_ are you staking (e.g. "Pool XYZ" or "My Raspberry Pi") and confirm by clicking `Enable Cold Staking` button
{{< /tab >}}

{{< /tabs >}}

Now we've manged to connect your wallet to the Staking Node (your DSD or Pool of your choice).

With this setup, each time a bunch of your coins stake, they will get "moved" to the Staking Node and start staking on it. This is the best way to move your coins naturally to the Staking Node, especially if you are privacy-conscious.

## Zapping coins

If you want or need to move your coins to the Staking Node right away, you can do that with "zapping". That is useful, when you have either a small amount of coins (that would take ages to stake by themselves) or when you can't have your main wallet online and staking 24/7.

{{< hint info >}}
**Keep in mind that this step is entirely optional**.\
Zapping coins only accelerates the whole process of moving your coins to the Staking Node.
{{< /hint >}}

{{< tabs "zapping-coins" >}}

{{< tab "Particl Desktop" >}}
### Particl Desktop

Again, zapping coins is very easy and straightforward in Particl Desktop:

1. Click on the `Zap` button on the cold staking widget
2. Click on `Zap to 100%` to initiate the "zapping" process

You should now see a new transaction in your History, which automatically moved your coins to the Staking Node.
{{< /tab >}}

{{< tab "Particl Core" >}}
### Particl Core

In Particl Core, we need to **enable Coin Control** first:

1. **Settings → Options…**
2. In the **Wallet** tab, check "Enable coin control features"
3. Confirm by clicking `OK`

Then **generate a new Receiving address**:

1. In **Receive** tab → click `Request payment`
2. Copy the generated address into your clipboard

**Send some small amount to your newly generated address using all available inputs**

1. In **Send** tab → under **Coin Control** Features click on `Inputs…`
2. Check all available inputs (you can click the `(un)select all` button) and confirm with `OK`
3. Copy your previously generated receiving address to the **Pay to** field (like if you would pay yourself)
4. Set the transaction amount to some small value (like 0.001 PART)
5. Click `Send`

This will send all but those 0.001 PART to the connected Staking Node.
{{< /tab >}}

{{< tab "Particl Copay" >}}
### Particl Copay

1. Open Particl Copay
2. Select your wallet from overview
3. Click on **Staking** tab/icon in the bottom navigation
4. You should see a "Wallet is staking" screen → click the `Zap` button
5. New window appears, confirm the action by clicking on `Zap` again
6. Confirm the transaction fee for zapping → `Proceed`
7. Enter your password/fingerprint for sending transactions

The zap transaction is now being sent and your coins are successfully on Staking Node.
{{< /tab >}}

{{< /tabs >}}

## Sending Individual Outputs

### Particl-Qt

- Enable [Coin Control](/tutorial/privacy/coin-control/)
- Generate a spending key
  - On the **Receive** tab set the drop down next to the `Create new receiving address` button to "Standard 256bit", click the button and copy the address.
- On the **Send** tab click the `Add Coldstake Recipient` button.  The form should change.
  - Insert the 256bit address you've created in the "Spend Address" edit box.
  - Insert the pool address or your staking node address in the "Stake Address" edit box.
- Select the output/s you want to send from coincontrol.
- Input the amount you want to send (send the entire output by clicking `Use available balance` and selecting `Subtract fee from amount`.
- Click `Send`

### particld

- Run `listunspent`, copy the "txid", "vout" and "amount" of the output you want to send.
- Generate a spending key
  - Run `getnewaddress "label" false false true`
- Run `buildscript "{\"recipe\":\"ifcoinstake\",\"addrstake\":\"STAKE_ADDRESS\",\"addrspend\":\"256BIT_ADDRESS\"}"`
  - Copy the "hex" field
- Run `sendtypeto part part "[{\"address\":\"script\",\"amount\":AMOUNT,\"subfee\":true,\"script\":\"HEX_FROM_BUILDSCRIPT\"}]" "" "" 5 1 false "{\"inputs\":[{\"tx\":\"TXID\",\"n\":VOUT}]}"`
