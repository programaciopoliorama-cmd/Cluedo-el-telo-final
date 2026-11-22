# Teló Final

Joc tipus Cluedo per al dinar del Poliorama: un assassinat la nit d'estrena. Web estàtica (HTML + JS) amb la base de dades a Supabase.

## Pàgines

| Pàgina | Per a qui | Adreça |
|---|---|---|
| `index.html` | Jugadors (mòbil) | `/` o `/?c=CODI` |
| `master.html` | Màster (Laia) | `/master` |
| `pantalla.html` | Projector | `/pantalla?k=…` (l'enllaç surt al panell del màster) |

## Com es juga una partida

1. Obre `/master`. La primera vegada et demana crear la contrasenya de màster.
2. Escriu els noms (un per línia) i prem **Repartir personatges**. Cada persona rep un personatge a l'atzar i un codi de 4 lletres.
3. Prem **Imprimir codis** per tenir un tiquet per persona amb el QR, o ensenya el QR des del panell.
4. Obre l'enllaç **Pantalla gran** a l'ordinador del projector.
5. Avança les fases amb els botons: Aperitiu → 1r acte → Entreacte (surt l'informe forense) → 2n acte (l'assassina pot enviar un rumor; tu l'aproves) → Obrir votació → Tancar votació.
6. Marca **Mostrar la solució a la pantalla gran** i fes la revelació pas a pas (clic o barra espaiadora). Quan vulguis, marca també **als mòbils**.
7. Per a una partida nova: **Reiniciar la partida**.

Durant la partida pots afegir algú que arriba tard, treure qui no ve o canviar el nom d'un personatge (per passar-lo a una altra persona).

## Publicar a Vercel

1. Puja aquesta carpeta al repositori de GitHub.
2. A vercel.com: **Add New → Project → Import** el repositori. Framework: *Other*. Sense build command. Output directory: l'arrel.
3. Cada vegada que facis *push* a GitHub, Vercel publica la versió nova.

## Base de dades

Projecte Supabase **cluedo-telo-final** (organització Teatre Poliorama). Tota la informació secreta (solució, fitxes) és en un esquema privat i només es pot llegir a través de funcions que comproven el codi del jugador o la contrasenya del màster. A `js/config.js` hi ha la URL i la clau *publishable*, que són públiques.

## Llibreries

`vendor/supabase.js` (supabase-js 2.45.4) i `vendor/qrcode.js` (qrcode-generator 1.4.4) són còpies locals, perquè la web no depengui de cap CDN.
