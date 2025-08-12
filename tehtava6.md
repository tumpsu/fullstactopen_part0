sequenceDiagram
    participant browser
    participant server

    Note over browser: Käyttäjä kirjoittaa muistiinpanon ja painaa "Save"

    browser->>browser: JavaScript käsittelee lomakkeen tapahtuman
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: 201 Created (tai vastaava kuittaus)
    deactivate server

    Note over browser: JavaScript päivittää muistiinpanolistan ilman sivun uudelleenlatausta
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Päivitetty JSON-muistiinpanolista
    deactivate server

    browser->>browser: DOM päivittyy uudella muistiinpanolla
