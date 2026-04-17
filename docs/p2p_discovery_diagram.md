sequenceDiagram
    participant A as Actor A
    participant BS as Base Station
    participant B as Actor B

    rect rgba(120,120,120,0.08)
        Note over A,B: Bootstrap via Base Station
        B->>BS: REQUEST {iceServers}
        BS-->>B: RESPOND {iceServers}
        B->>BS: PUBLISH {kid, encap offer}
        A->>BS: REQUEST {offer}
        BS-->>A: RESPOND {kid, encap offer}
    end

    rect rgba(120,120,120,0.08)
        Note over A,B: Unauthenticated P2P authentication exchange
        A->>B: 1. Send {pseudonym, challenge}
        B->>A: 2. Send {pseudonym, challenge, assertion}
        A->>B: 3. Send {assertion}
    end

    Note over A,B: Authenticated P2P connection established
