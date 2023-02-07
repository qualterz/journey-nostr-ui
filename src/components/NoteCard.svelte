<script lang="ts">
  export let content: string;
  export let authorName: string | null = null;
  export let authorAvatarUrl: string | null = null;
  export let authorUrl: string | null = null;
  export let timestamp: Date | null = null;
</script>

<div class="card">
  <div class="card-body">
    {#if authorName || authorAvatarUrl || timestamp}
      <div class="d-flex align-items-center mb-3">
        {#if authorAvatarUrl}
          <span
            class="avatar avatar-sm rounded-circle"
            style="background-image: url({authorAvatarUrl});"
          />
        {:else if authorName}
          <span class="avatar avatar-sm rounded-circle">
            {authorName[0]}
          </span>
        {/if}

        {#if authorName && authorUrl}
          <div class="ms-1 fw-bold"><a class="text-reset" href={authorUrl}>{authorName}</a></div>
        {:else if authorName}
          <div class="ms-1 fw-bold">{authorName}</div>
        {/if}

        {#if timestamp}
          <div class="ms-auto text-muted">
            {timestamp.toLocaleDateString()} -
            {timestamp.toLocaleTimeString()}
          </div>
        {/if}
      </div>
    {/if}
    <p style="white-space: pre-line">
      {content}
    </p>
  </div>
</div>
