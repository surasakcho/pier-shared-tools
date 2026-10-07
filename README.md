# pier-shared-tools

The programs that open a PIER data package: a converter (`CONVERT`) and, for
an encrypted package, a decrypter (`DECRYPT`), with the programs they run.
They work on Windows, macOS and Linux, and need no Python.

You only need this if a PIER data package told you to. The package's own
`README.txt` names the exact version you need, with the file name, the link
and the checksum to expect. This repository holds only this README, the
licences and the releases. It holds no data.

## What you download

Each release (under **Releases**, tagged `v<version>`) has four files:

| file | for |
|---|---|
| `pier-shared-tools-<version>-windows.zip` | Windows (about 14 MB) |
| `pier-shared-tools-<version>-macos.zip` | macOS, Intel and Apple silicon (about 38 MB) |
| `pier-shared-tools-<version>-linux.zip` | Linux, 64-bit x86 (about 22 MB) |
| `SHA256SUMS.txt` | the SHA-256 of each zip |

Download the zip for your computer, and only that one. Use the **exact
version your package names**: `CONVERT` and `DECRYPT` refuse to run on any
other version, and print the link to the right one. Older releases stay here,
so an old package can always get the version it names.

## Check the download

Run the command for your system, in the folder you downloaded the zip to, and
compare the result with the value in your package's `README.txt` (or in the
release's `SHA256SUMS.txt`). If they differ, delete the file and download it
again.

    certutil -hashfile pier-shared-tools-<version>-windows.zip SHA256
    shasum -a 256 pier-shared-tools-<version>-macos.zip
    sha256sum pier-shared-tools-<version>-linux.zip

## Use it

1. Unzip it into the package folder, the one that holds the package's
   `README.txt`, `data/` (or `data.7z`, or `data.7z.001` and the volumes after
   it) and `sql/`. Do not unzip it into a new folder inside it.
2. On macOS, clear the quarantine mark that a download puts on every file,
   once, in Terminal, from inside the package folder (this covers the programs
   in `tools/` as well as `CONVERT.command` and `DECRYPT.command`):

       xattr -dr com.apple.quarantine .

3. Run `CONVERT` (`CONVERT.bat`, `CONVERT.command` or `CONVERT.sh`). For an
   encrypted package (`data.7z`), run `DECRYPT` first and have the passphrase
   you were sent separately ready.

If you cannot reach GitHub, ask the person who sent the package for the zip by
another channel, and check it with the same command.

## What is in each zip

- the launchers for that system: `CONVERT` and `DECRYPT`;
- `tools/duckdb/` and `tools/7zip/`: the programs they run, unmodified;
- `licenses/`: the licence texts of those programs;
- `VERSION`: the shared tools version, which the launchers compare with the
  one your package names.

## Licences

The zips redistribute two programs, unmodified, under their own licences. The
texts are in each zip, under `licenses/`.

- **DuckDB** command-line shell, MIT licence. Copyright Stichting DuckDB
  Foundation. https://duckdb.org
- **7-Zip** command-line program, GNU LGPL (with the unRAR licence
  restriction for some code, and the BSD 3-clause licence for some code).
  Copyright Igor Pavlov. https://www.7-zip.org

The launchers (`CONVERT` and `DECRYPT`) are scripts written for the PIER data
package; each release's notes say what it contains.

## Versions

| shared tools | DuckDB | 7-Zip |
|---|---|---|
| 1.0.0 | v1.5.5 | 23.01 |
