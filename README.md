# SV5BYP's Cat Bridge

<img src="icon.png" alt="Cat Bridge" width="160">

**A Logger32 utility for connecting radio applications.**

Cat Bridge connects Logger32 to FT8, SSTV and other Windows applications that support **Ham Radio Deluxe**, **OmniRig Rig 1** or **Hamlib NET rigctl**. Logger32 keeps the physical CAT connection and the selected radio driver. Cat Bridge translates the supported application requests between the programs and Logger32.

**[Download the latest release](https://github.com/sv5byp/Cat-Bridge/releases/latest)**

Choose the full **SV5BYP-Cat-Bridge-…zip** under **Assets**. The `.bin` and `.sig` files are for the built-in updater and do not need to be opened manually.

## Before using Cat Bridge

**First confirm that both frequency control and PTT already work between Logger32 and your radio.**

1. Turn on the radio, connect it to the computer, and configure the correct radio model and connection in Logger32.
2. Confirm that Logger32 reads the radio's frequency correctly and that changing the frequency in Logger32 tunes the radio.
3. Open Logger32's **Soundcard Data** window and check PTT using the configured radio/PTT interface. Confirm on the physical radio that it enters transmit when PTT is activated and returns to receive when PTT is released. A displayed acknowledgement alone does not confirm physical transmission.
4. Once these checks pass, start Cat Bridge and connect your FT8, SSTV or other application to it.

If frequency control or PTT does not work in Logger32, resolve that radio/interface configuration first. Cat Bridge relies on this working connection to link Logger32 with the other applications.

## Getting started

1. Complete the Logger32 frequency and PTT checks above.
2. Extract **all** files from the ZIP into one permanent folder, for example `C:\CatBridge`. Do not run inside the ZIP.
3. Run `SV5BYP's Cat Bridge.exe`. It starts minimized and connects to Logger32 automatically.
4. Keep your preferred connection type in the other application:

| Application setting | Connection |
| --- | --- |
| Ham Radio Deluxe | `127.0.0.1:7809`, or compatibility port `127.0.0.1:4533` |
| Hamlib NET rigctl | `127.0.0.1:4533` |
| OmniRig | **Rig 1**, with **CAT PTT** |

The two network protocols are recognized automatically per connection. For OmniRig, a clean first installation sets up the adapter automatically. If another OmniRig route already exists, Cat Bridge asks once before changing the current-user route and retains its previous configuration for restoration. Close OmniRig applications before accepting that change; if they were open, restart Cat Bridge after closing them to complete setup. Updating the same permanent folder preserves existing activation.

## Start automatically with Logger32

**Cat Bridge is a utility for Logger32.** To have it start automatically whenever Logger32 starts, add `SV5BYP's Cat Bridge.exe` to Logger32's utility program list and tick its entry in Logger32's **Utilities menu**.

Use the full path to the EXE in the permanent folder where you extracted Cat Bridge. Keep that folder in the same location when updating so the saved utility entry continues to point to the program. On the next Logger32 startup, Cat Bridge will launch automatically and start minimized.

## PTT and shared control

- **PTT…** offers Logger32 PTT, a separate physical serial port with DTR or RTS, or Off. The optional PTT port must be separate from Logger32's CAT port.
- Working frequency control alone does not establish PTT support. Logger32 must accept its external PTT requests, or an appropriate separate PTT interface is needed.
- Reading frequency does not reserve control. The first actual frequency change or PTT request takes control until that application's connection closes. Other applications may continue reading.
- Only the service that currently owns control is green. A passive reader remains neutral.
- The continuous PTT limit is **three minutes** for every connection type.
- Ordinary Logger32 connection failures retry automatically without an attempt limit. Recovery does not automatically replay a previous transmission.

## Automatic program updates

Automatic updates are enabled by default. Cat Bridge checks the official stable GitHub release shortly after startup, then every six hours. The **⋯** menu contains **Check for updates**, **Automatic updates**, **About • Logger32 utility** and the official download link.

A newer release is downloaded and its pinned publisher signature is verified. Installation waits until applications using the bridge disconnect; it does **not** interrupt a transmission or terminate an application during an RX gap. Close the connected FT8/SSTV/CAT programs when convenient, and Cat Bridge can install the prepared update and restart itself. **Logger32 stays open.**

Only the running Cat Bridge installation is updated. Saved PTT choices and OmniRig activation are retained. Program backups and recovery of an interrupted installation are provided. No personal Logger32 data, QSO logs or settings files are part of the update payload. Automatic network errors are recorded in the diagnostic log without interrupting CAT/PTT.

**First upgrade from 3.28 or earlier:** download and extract the complete new ZIP manually. Close the old Bridge and its client applications, then replace all release files in the same permanent folder. Do not remove existing activation backups or personal files. Future releases can then use the built-in updater.

## Antivirus compatibility

Some antivirus products may flag or block Cat Bridge. Blocking can prevent startup, interrupt CAT/PTT communication, or prevent optional error reports from being sent.

If this happens, review the antivirus detection and verify that the affected file matches the official Cat Bridge release. A targeted scanning exception for the verified `SV5BYP's Cat Bridge.exe` may be needed. Keep antivirus protection enabled and limit the exception to the verified program file. If connections or report sending remain blocked, also review the antivirus network protection settings for Cat Bridge. Automatic error reporting still requires the user's consent.

Suspected false detections can be submitted to the antivirus vendor for review; for AVG, use its [official false-positive report form](https://www.avg.com/en-us/report-false-positive).

## Compatibility and help

Configure the actual radio only in Logger32. Support depends on its working driver and PTT configuration; this utility does not certify every radio model. The bridge provides the existing primary/simplex frequency and PTT functions. OmniRig Rig 2, split operation and raw/custom CAT commands are outside that interface. Use **Mode None / Split None** in clients that offer these settings, and select the operating mode in Logger32 or on the radio.

The panel and controls are in English. English and Greek instructions are included in the download. Full diagnostics are saved under `%LOCALAPPDATA%\SV5BYP\Cat Bridge\Diagnostics`.

Cat Bridge is an independent SV5BYP utility, not an official product of Logger32, Ham Radio Deluxe, OmniRig or Hamlib. No GitHub account is required to download a public release.
